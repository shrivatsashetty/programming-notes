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

## Embedding files in markdown
Markdown itself does not natively support embedding PDFs like it does with images. However, you can achieve similar functionality using different methods depending on where you are rendering the Markdown.

### **1. Using an HTML `<iframe>` (Works in some Markdown renderers)**
```markdown
<iframe src="your-file.pdf" width="100%" height="600px"></iframe>
```
This works in environments that support HTML inside Markdown, such as GitHub Pages, some wikis, or web-based Markdown renderers.

---

### **2. Linking to the PDF (Universal)**
If embedding is not possible, you can provide a direct link to the PDF:
```markdown
[View PDF](your-file.pdf)
```
Clicking the link will open the PDF in the browser.

---

### **3. Using PDF.js (For Web-based Markdown)**
If you're working in a web-based environment, you can use Mozilla's PDF.js to embed the PDF:
```markdown
<iframe src="https://mozilla.github.io/pdf.js/web/viewer.html?file=your-file.pdf" width="100%" height="600px"></iframe>
```
Replace `your-file.pdf` with the actual file path.

---

### **4. Embedding in Jupyter Notebook (For Markdown in Jupyter)**
If you're using Markdown inside a Jupyter Notebook, you can use IPython’s display utilities:
```python
from IPython.display import IFrame
IFrame("your-file.pdf", width=600, height=300)
```