@@Title=Resolving Slow Performance of NSTextStorage
@@Date=Friday, 20 July 2018

I spent a couple hours yesterday attempting to resolve some performance issues when adding some basic syntax highlighting to a `UITextView`. I'll write about what I'm working on at a later date, but I want to take this moment to document how I resolved the issue.

**TLDR:   The problem is Swift. Write the `NSTextStorage` in Objective-C.  Explanation and code sample below.**

## The Problem
As of iOS 7, text is rendered in standard UIKit controls via a system called TextKit. The framework allows for all kinds of fancy things including, of interest to my project, a way to style text attributes based on the text syntax. Like code syntax highlighting but based on arbitrary syntactical rules. 

Looking it up, the proper way to achieve this is by subclassing `NSTextStorage` of a `UITextView`.  There's lot's of [online tutorials](https://www.raywenderlich.com/50151/text-kit-tutorial) explaining how to do this. 

However, the textview performed terribly when I pasted in a lot of text (I used the full script of "A Streetcar Named Desire", which is a couple thousand lines).  It was not my syntax rules that were the problem either. Merely subclassing `NSTextStorage`, doing nothing fancy, was causing the app to lag and crash, outputting the opaque message in the debugger "Terminated due to memory error".

## The Solution
[Some folks online](https://stackoverflow.com/questions/37952726/sub-classing-nstextstorage-causes-significant-memory-issues) were helped by changing the internal store from a `NSAttributedString` to `NSTextStorage`, but for me the problem remained. 

The solution that did work for me? **Write the subclass in Objective-C**.  

At first I didn't know why this worked, but looking into it further, I believe it comes down to the conversion between Swift's `String` and Objective-C's `NSString`. The two have basically the same interface, but to convert between the two is not a constant time operation. Apparently, the conversion is O(n), leading to performance problems with very large amounts to text.  

There's perhaps more to it, but that's all I could think of given my relatively limited knowledge on this stuff. Regardless, problem solved!


## Objective-C Code Sample

#### CustomTextStorage.h

```objc

#import <UIKit/UIKit.h>

@interface ImportTextStorage : NSTextStorage

@end

```

#### CustomTextStorage.m

```objc

#import "CustomTextStorage.h"

@interface CustomTextStorage ()
@property (nonatomic) NSTextStorage *storage;
@end

@implementation CustomTextStorage

@synthesize storage = _storage;


- (instancetype)init {
    if (self = [super init]) {
        self.storage = [[NSTextStorage alloc] init];
    }
    return self;
}



- (NSString *)string {
    return self.storage.string;
}

- (NSDictionary<NSString *,id> *)attributesAtIndex:(NSUInteger)location effectiveRange:(NSRangePointer)effectiveRange {
    return [self.storage attributesAtIndex:location effectiveRange:effectiveRange];
}

- (void)replaceCharactersInRange:(NSRange)range withString:(NSString *)aString {
    [self.storage replaceCharactersInRange:range withString:aString];
    [self edited:NSTextStorageEditedCharacters range:range
         changeInLength:aString.length - range.length];
}

- (void)setAttributes:(NSDictionary<NSString *,id> *)attributes range:(NSRange)range {
    [self beginEditing];
    [self.storage setAttributes:attributes range:range];
    [self edited:NSTextStorageEditedAttributes range:range changeInLength:0];
    [self endEditing];
}

- (void)processEditing {
    //
    // Apply Custom Styling Here!
    //
    [super processEditing];
}

@end

```


