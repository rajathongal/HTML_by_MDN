# What structure should your website have?

The most common things we'll have on any website project we create are an index HTML file and folders to contain images, style files, and script files.

- **index.html**: This file will generally contain your homepage content, that is, the text and images that people see when they first go to your site. Using your text editor, create a new file called index.html and save it just inside your test-site folder.
- **images folder**: This folder will contain all the images that you use on your site. Create a folder called images, inside your test-site folder.
- **styles folder**: This folder will contain the CSS code used to style your content (for example, setting text and background colors). Create a folder called styles, inside your test-site folder.
- **scripts folder**: This folder will contain all the JavaScript code used to add interactive functionality to your site (e.g. buttons that load data when clicked). Create a folder called scripts, inside your test-site folder.

some color code #95E8B8

## HTML (HyperText Markup Language)

HTML is the code that is used to structure a web page and its content. For example, content could be structured within a set of paragraphs, a list of bulleted points, or using images and data tables. As the title suggests, this article will give you a basic understanding of HTML and its functions.

HTML is a markup language that defines the structure of your content. HTML consists of a series of elements, which you use to enclose, or wrap, different parts of the content to make it appear a certain way, or act a certain way. The enclosing tags can make a word or image hyperlink to somewhere else, can italicize words, can make the font bigger or smaller, and so on. For example, take the following line of content:

My cat is very grumpy

If we wanted the line to stand by itself, we could specify that it is a paragraph by enclosing it in paragraph tags:

```HTML
<p>My cat is very grumpy</p>
```

## Anatomy of an HTML element

The main parts of our element are as follows:

- The opening tag: This consists of the name of the element (in this case, p), wrapped in opening and closing angle brackets. This states where the element begins or starts to take effect — in this case where the paragraph begins.
- The closing tag: This is the same as the opening tag, except that it includes a forward slash before the element name. This states where the element ends — in this case where the paragraph ends. Failing to add a closing tag is one of the standard beginner errors and can lead to strange results.
- The content: This is the content of the element, which in this case, is just text.
- The element: The opening tag, the closing tag, and the content together comprise the element.

**Attributes** contain extra information about the element that you don't want to appear in the actual content. Here, class is the attribute name and editor-note is the attribute value. The class attribute allows you to give the element a non-unique identifier that can be used to target it (and any other elements with the same class value) with style information and other things. Some attributes have no value, such as required.

Attributes that set a value always have:

- A space between it and the element name (or the previous attribute, if the element already has one or more attributes).
- The attribute name followed by an equal sign.
- The attribute value wrapped by opening and closing quotation marks.

## Nesting elements

You can put elements inside other elements too — this is called nesting. If we wanted to state that our cat is very grumpy, we could wrap the word "very" in a <strong> element, which means that the word is to be strongly emphasized:

```HTML
<p>My cat is <strong>very</strong> grumpy.</p>
```

## Void elements

Some elements have no content and are called void elements. Take the <img> element that we already have in our HTML page:

```HTMl
<img src="images/firefox-icon.png" alt="My test image" />

```

This contains two attributes, but there is no closing </img> tag and no inner content. This is because an image element doesn't wrap content to affect it. Its purpose is to embed an image in the HTML page in the place it appears.

## Anatomy of an HTML document

Let's revisit the code we put into our index.html

```HTML

<!doctype html>
<html lang="en-US">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Brave Browser</title>
  </head>
  <body>
    <img src="./images/browserLogo.png" alt="Brave Browser" />
  </body>
</html>

```

- <!DOCTYPE html> — doctype. It is a required preamble (Introductory line). In the mists of time, when HTML was young (around 1991/92), doctypes were meant to act as links to a set of rules that the HTML page had to follow to be considered good HTML, which could mean automatic error checking and other useful things. However, these days, they don't do much and are basically just needed to make sure your document behaves correctly. That's all you need to know for now.

- <html></html> — the <html> element. This element wraps all the content on the entire page and is sometimes known as the root element. It also includes the lang attribute, setting the primary language of the document.

- <head></head> — the <head> element. This element acts as a container for all the stuff you want to include on the HTML page that isn't the content you are showing to your page's viewers. This includes things like keywords and a page description that you want to appear in search results, CSS to style our content, character set declarations, and more.

- <meta charset="utf-8"> — This element sets the character set your document should use to UTF-8 which includes most characters from the vast majority of written languages. Essentially, it can now handle any textual content you might put on it. There is no reason not to set this, and it can help avoid some problems later on.

- <meta name="viewport" content="width=device-width"> — This viewport element ensures the page renders at the width of viewport, preventing mobile browsers from rendering pages wider than the viewport and then shrinking them down.

- <title></title> — the <title> element. This sets the title of your page, which is the title that appears in the browser tab the page is loaded in. It is also used to describe the page when you bookmark/favorite it.

- <body></body> — the <body> element. This contains all the content that you want to show to web users when they visit your page, whether that's text, images, videos, games, playable audio tracks, or whatever else.

## Comments in HTML

Note: Anything in HTML between <!-- and --> is an HTML comment. The browser ignores comments as it renders the code. In other words, they are not visible on the page - just in the code.

## Marking up text

This section will cover some essential HTML elements you'll use for marking up the text.

### Headings

Heading elements allow you to specify that certain parts of your content are headings — or subheadings. In the same way that a book has the main title, chapter titles, and subtitles, an HTML document can too. HTML contains 6 heading levels, <h1> - <h6>, although you'll commonly only use 3 to 4 at most:

```HTML
<!-- 4 heading levels: -->
<h1>My main title</h1>
<h2>My top level heading</h2>
<h3>My subheading</h3>
<h4>My sub-subheading</h4>
```

### Paragraphs

As explained above, <p> elements are for containing paragraphs of text; you'll use these frequently when marking up regular text content:

```HTML
<p>This is a single paragraph</p>
```

### Lists

A lot of the web's content is lists and HTML has special elements for these. Marking up lists always consists of at least 2 elements. The most common list types are ordered and unordered lists:

- Unordered lists are for lists where the order of the items doesn't matter, such as a shopping list. These are wrapped in a <ul> element.
- Ordered lists are for lists where the order of the items does matter, such as a recipe. These are wrapped in an <ol> element.

Each item inside the lists is put inside an <li> (list item) element.

For example, if we wanted to turn the part of the following paragraph fragment into a list

```HTML
<p>
  At Mozilla, we're a global community of technologists, thinkers, and builders
  working together…
</p>
```

We could modify the markup to this

```HTML
<p>At Mozilla, we're a global community of</p>

<ul>
  <li>technologists</li>
  <li>thinkers</li>
  <li>builders</li>
</ul>

<p>working together…</p>
```

### Links

Links are very important — they are what makes the web a web! To add a link, we need to use a simple element — <a> — "a" being the short form for "anchor". To make text within your paragraph into a link, follow these steps:

- Choose some text. We chose the text "Brave Manifesto"
- Wrap the text in an <a> element, as shown below

```HTML
<a>Mozilla Manifesto</a>
```

- Give the <a> element an href attribute, as shown below:

```HTML
<a href="">Mozilla Manifesto</a>
```

- Fill in the value of this attribute with the web address that you want the link to:

```HTML
<a href="https://www.mozilla.org/en-US/about/manifesto/">
  Mozilla Manifesto
</a>
```

**href - Hypertext Reference**

You might get unexpected results if you omit the https:// or http:// part, called the protocol, at the beginning of the web address. After making a link, click it to make sure it is sending you where you wanted it to.

## CSS basics

CSS (Cascading Style Sheets) is the code that styles web content.

### What is CSS?

Like HTML, CSS is not a programming language. It's not a markup language either. CSS is a style sheet language. CSS is what you use to selectively style HTML elements. For example, this CSS selects paragraph text, setting the color to red:

```CSS
p {
  color: red;
}

```

Let's try it out! Using a text editor, paste the three lines of CSS (above) into a new file. Save the file as style.css in a directory named styles.

To make the code work, we still need to apply this CSS (above) to your HTML document. Otherwise, the styling won't change the appearance of the HTML.

Open your index.html file. Paste the following line in the head (between the <head> and </head> tags):

```HTML
<link href="styles/style.css" rel="stylesheet" />
```

### Anatomy of a CSS ruleset

The whole structure is called a ruleset. (The term ruleset is often referred to as just rule.) Note the names of the individual parts:

- Selector
This is the HTML element name at the start of the ruleset. It defines the element(s) to be styled (in this example, <p> elements). To style a different element, change the selector.

- Declaration
This is a single rule like color: red;. It specifies which of the element's properties you want to style.

- Properties
These are ways in which you can style an HTML element. (In this example, color is a property of the <p> elements.) In CSS, you choose which properties you want to affect in the rule.

- Property value
To the right of the property—after the colon—there is the property value. This chooses one out of many possible appearances for a given property. (For example, there are many color values in addition to red.)

Note the other important parts of the syntax:

- Apart from the selector, each ruleset must be wrapped in curly braces. ({})
- Within each declaration, you must use a colon (:) to separate the property from its value or values.
- Within each ruleset, you must use a semicolon (;) to separate each declaration from the next one.

To modify multiple property values in one ruleset, write them separated by semicolons, like this:

```CSS
p {
  color: red;
  width: 500px;
  border: 1px solid black;
}

```

### Selecting multiple elements

You can also select multiple elements and apply a single ruleset to all of them. Separate multiple selectors by commas. For example:

```CSS
p,
li,
h1 {
  color: red;
}
```

### Different types of selectors

There are many different types of selectors. The examples above use element selectors, which select all elements of a given type. But we can make more specific selections as well. Here are some of the more common types of selectors:

| Selector name                       | What does it select                                         | Example                                     |
| ------------------------------------|-------------------------------------------------------------|---------------------------------------------|
| Element selector (tag/type selector) | All HTML elements of the specified type.                    | `p` selects `<p>`                           |
| ID selector                          | The element on the page with the specified ID.              | `#my-id` selects `<p id="my-id">` or `<a id="my-id">` |
| Class selector                       | The element(s) on the page with the specified class.        | `.my-class` selects `<p class="my-class">` and `<a class="my-class">` |
| Attribute selector                   | The element(s) on the page with the specified attribute.    | `img[src]` selects `<img src="myimage.png">` but not `<img>` |
| Pseudo-class selector                | The specified element(s), but only when in the specified state. (e.g., when a cursor hovers over a link.) | `a:hover` selects `<a>`, but only when the mouse pointer is hovering over the link. |

### CSS layout

is mostly based on the box model. Each box taking up space on your page has properties like:

padding, the space around the content. In the example below, it is the space around the paragraph text.
border, the solid line that is just outside the padding.
margin, the space around the outside of the border.

## JavaScript basics

JavaScript is a programming language that adds interactivity to your website. This happens in games, in the behavior of responses when buttons are pressed or with data entry on forms; with dynamic styling; with animation, etc.
