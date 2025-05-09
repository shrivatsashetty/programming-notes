# Markdown Guide

## Links to the Official Documentation
- [Getting Started](https://www.markdownguide.org/getting-started/)
- [Basic Syntax](https://www.markdownguide.org/basic-syntax/)
- [Extended Syntax](https://www.markdownguide.org/extended-syntax/)
- [Quick Hands On Tutorial](https://www.markdowntutorial.com/)

## Bold & Italics
- To make text _italic_, place an underscore("_") symbol on either side of the text.
- To make a text **bold**, place a double asterisk("**") on either side of the text.
- We can use them in combination to make the text both **_Italicised and Bold_**. <br>
  The order in which we place the double asterisk and underscores does not matter.

## Headers
 Headers are used to denote page headings, section headings or to draw attention of the viewer to a particular section of the page. <br>
 Depending on the size, headers range from h1 to h6. To turn the text into a headedr text, place a hash mark ("#") preceeding the text <br>
 The no of hash marks placed will determine the size of the header. We can also mix other markdown syntaxes like bold or italics with headers.
# Normal h1
## **Bold h2**
### _Italic h3_
#### [Hyperlink h4](https://www.lipsum.com/)
##### `Embedded h5`
###### ~~Strikethrough h6~~

## Links
 There are two types of links links in markdown:

### 1. Inline Links
 To create an inline link, you wrap the link text in brackets ( [ ] ), and then you wrap the link in parentheses ( ( ) ). For example, a hyperlink to www.github.com, with a link text that says, "Visit GitHub!" looks something like this: [Visit GitHub](https://www.github.com) We can also make links with heading along with some formatting to the link text as follows: 
 #### The Latest News from [_The_ **BBC**](https://www.bbc.com/news)

### 2. Reference Link
As the name implies, the link is actually a reference to another place in the document. The "references" above are the second set of brackets: `[another place]` and `[another-link]`. At the bottom of a Markdown document, these brackets are defined as proper links to outside websites. An advantage of the reference link style is that multiple links to the same place only need to be updated once. For example, if we decide to make all of the `[another place]` links go somewhere else, we only have to change the single reference link.

Reference links don't appear in the rendered Markdown. You define them by providing the same tag name wrapped in brackets, followed by a colon, followed by the link.

Do you want to [search anything][google search] ?

Or do you prefer learn from [youtube] ?

[google search]: https://www.google.com
[youtube]: https://www.youtube.com

## Images
The first image style is called an inline image link. To create an inline image link, enter an exclamation point (`!`), wrap the alt text in brackets (`[ ]`), and then wrap the link in parentheses (`( )`) as follows: <br>
![A pretty tiger](https://upload.wikimedia.org/wikipedia/commons/5/56/Tiger.50.jpg)

The images can be referenced usigng a hyperlink or may be coming from a file in your computer in which case you need to specify the absolute path of the image file in your computer or an relative path relative to the markdown file:<br>
![Orange Cat](./Assets/Images/orange_cat.png)

For a reference image, you'll follow the same pattern as a reference link. You'll precede the Markdown with an exclamation point, then provide two brackets for the alt text, and then two more for the image tag, as follows: [Black cat][Black]

[Black]: https://upload.wikimedia.org/wikipedia/commons/a/a3/81_INF_DIV_SSI.jpg

## Blockquotes
A blockquote is a sentence or paragraph that's been specially formatted to draw attention to the reader. To create a block quote, all you have to do is preface a line with the "greater than" caret (`>`). For example:
> "The sin of doing nothing is the deadliest of all the seven sins. It has been said that for evil men to accomplish their purpose it is only necessary that good men should do nothing."

You can also place a caret character on each line of the quote. This is particularly useful if your quote spans multiple paragraphs. For example:
> His words seemed to have struck some deep chord in his own nature. Had he spoken
  of himself, of himself as he was or wished to be? Stephen watched his face for some
  moments in silence. A cold sadness was there. He had spoken of himself, of his own
  loneliness which he feared.
>
> —Of whom are you speaking? Stephen asked at length.
>
> Cranly did not answer.

Block quotes can contain other Markdown elements, such as italics, images, or links.
>There were four French delegates in a brake and one, a plump smiling young man, held, wedged on a stick, a card on which were printed the words: _VIVE L'IRLANDE_!

Alerts are special type of blockquotes. They are an extension of Markdown used to emphasize critical information. On GitHub, they are displayed with distinctive colors and icons to indicate the importance of the content.

An example of all five types:

> [!NOTE]  
> Highlights information that users should take into account, even when skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]  
> Crucial information necessary for users to succeed.

> [!WARNING]  
> Critical content demanding immediate user attention due to potential risks.

> [!CAUTION]
> Negative potential consequences of an action.