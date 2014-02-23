Creating attributed strings is a laborious task. In addition, you commonly want to display some rich text from an API like Facebook or Twitter which is marked up using HTML. For an example, one of the API responses might contain a snippet like the following:

```
This is <b>bold</b>
```

### A Simple Solution in iOS 7

If you're targeting iOS 7 and above and your text layout needs are simple, there's an easy solution that doesn't require any external libraries.

```
// This is a string that you might find in your model
NSString *html = @"This is <b>bold</b>";
    
// Apply some inline CSS
NSString *styledHtml = [self styledHTMLwithHTML:html];
    
// Generate an attributed string from the HTML
NSAttributedString *attributedText = [self attributedStringWithHTML:styledHtml];
    
// Set the attributedText property of the UILabel
label.attributedText = attributedText;
```

The snippet above assumes that you've declared the helper methods below. Use whatever CSS style you like to easily control the text styling. Unfortunately, it's not well documented what subset of CSS is supported, but many simple styles are supported.

```
- (NSString *)styledHTMLwithHTML:(NSString *)HTML {
    NSString *style = @"<style> body { font-family: 'HelveticaNeue'; font-size: 20px; } b {font-family: 'MarkerFelt-Wide'; }</style>";
    
    return [NSString stringWithFormat:@"%@%@", style, HTML];
}

- (NSAttributedString *)attributedStringWithHTML:(NSString *)HTML {
    NSDictionary *options = @{ NSDocumentTypeDocumentAttribute: NSHTMLTextDocumentType };
    return [[NSAttributedString alloc] initWithData:[HTML dataUsingEncoding:NSUTF8StringEncoding] options:options documentAttributes:NULL error:NULL];
}
```

### Advanced Alternatives

Libraries such as [TTTAttributedLabel](https://github.com/mattt/TTTAttributedLabel) and [OHAttributedLabel](https://github.com/AliSoftware/OHAttributedLabel) have existed for many years to alleviate this problem, but slowly Apple is adding better native support for handling HTML, and TextKit in iOS 7 represents a giant leap forward in the amount of control iOS developers have in text layout.

For now, [DTCoreText](https://github.com/Cocoanetics/DTCoreText) remains the library to use for any iOS developer that wants serious control over their text.