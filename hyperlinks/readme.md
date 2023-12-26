# Creating HyperLinks

Hyperlinks allow us to link documents to other documents or resources, link to specific parts of documents, or make apps available at a web address. Almost any web content can be converted to a link so that when clicked or otherwise activated the web browser goes to another web address (URL).

Note: A URL can point to HTML files, text files, images, text documents, video and audio files, or anything else that lives on the Web.

## Anatomy of a link

A basic link is created by wrapping the text or other content inside an `<a>` element and using the href attribute, also known as a Hypertext Reference, or target, that contains the web address.

```HTML
<p>
  I'm creating a link to
  <a href="https://www.mozilla.org/en-US/">the Mozilla homepage</a>.
</p>
```

### Block level links

As mentioned before, almost any content can be made into a link, even block-level elements. If you want to make a heading element a link then wrap it in an anchor (`<a>`) element as shown in the following code snippet:

```HTML
<a href="https://developer.mozilla.org/en-US/">
  <h1>MDN Web Docs</h1>
</a>
<p>
  Documenting web technologies, including CSS, HTML, and JavaScript, since 2005.
</p>
```

### Image Links

If you have an image you want to make into a link, use the `<a>` element to wrap the image file referenced with the `<img>` element. The example below uses a relative path to reference a locally stored SVG image file.

```HTML
<a href="https://developer.mozilla.org/en-US/">
  <img src="mdn_logo.svg" alt="MDN Web Docs" />
</a>
```

### Adding supporting information with the title attribute

Another attribute you may want to add to your links is title. The title contains additional information about the link, such as which kind of information the page contains, or things to be aware of on the website.

Hover over the link to see what kind of information

```HTML
<p>
  I'm creating a link to
  <a
    href="https://www.mozilla.org/en-US/"
    title="The best place to find more information about Mozilla's
          mission and how to contribute">
    the Mozilla homepage</a>.
</p>
```

## A quick primer on URLs and paths

To fully understand link targets, you need to understand URLs and file paths. This section gives you the information you need to achieve this.

A URL, or Uniform Resource Locator is a string of text that defines where something is located on the Web. For example, Mozilla's English homepage is located at <https://www.mozilla.org/en-US/>.

URLs use paths to find files. Paths specify where the file you're interested in is located in the filesystem.

- Same directory: If you wanted to include a hyperlink inside index.html (the top level index.html) pointing to contacts.html, you would specify the filename that you want to link to, because it's in the same directory as the current file. The URL you would use is contacts.html:

```HTML
<p>
  Want to contact a specific staff member? Find details on our
  <a href="contacts.html">contacts page</a>.
</p>
```

- Moving down into subdirectories: If you wanted to include a hyperlink inside index.html (the top level index.html) pointing to projects/index.html, you would need to go down into the projects directory before indicating the file you want to link to. This is done by specifying the directory's name, then a forward slash, then the name of the file. The URL you would use is projects/index.html:

```HTML
<p>Visit my <a href="projects/index.html">project homepage</a>.</p>
```

- Moving back up into parent directories: If you wanted to include a hyperlink inside projects/index.html pointing to pdfs/project-brief.pdf, you'd have to go up a directory level, then back down into the pdfs directory. To go up a directory, use two dots — .. — so the URL you would use is ../pdfs/project-brief.pdf:

```HTML
<p>A link to my <a href="../pdfs/project-brief.pdf">project brief</a>.</p>
```

### Document fragments

It's possible to link to a specific part of an HTML document, known as a document fragment, rather than just to the top of the document. To do this you first have to assign an id attribute to the element you want to link to. It normally makes sense to link to a specific heading, so this would look something like the following:

```HTML
<h2 id="Mailing_address">Mailing address</h2>
```

Then to link to that specific id, you'd include it at the end of the URL, preceded by a hash/pound symbol (#), for example:

```HTML
<p>
  Want to write us a letter? Use our
  <a href="contacts.html#Mailing_address">mailing address</a>.
</p>
```

You can even use the document fragment reference on its own to link to another part of the current document:

```HTML
<p>
  The <a href="#Mailing_address">company mailing address</a> can be found at the
  bottom of this page.
</p>

```

### Absolute versus relative URLs

Two terms you'll come across on the Web are absolute URL and relative URL:

- absolute URL: Points to a location defined by its absolute location on the web, including protocol and domain name. For example, if an index.html page is uploaded to a directory called projects that sits inside the root of a web server, and the website's domain is <https://www.example.com>, the page would be available at <https://www.example.com/projects/index.html> (or even just <https://www.example.com/projects/>, as most web servers just look for a landing page such as index.html to load if it isn't specified in the URL.)

An absolute URL will always point to the same location, no matter where it's used.

- relative URL: Points to a location that is relative to the file you are linking from, more like what we looked at in the previous section. For example, if we wanted to link from our example file at <https://www.example.com/projects/index.html> to a PDF file in the same directory, the URL would just be the filename — project-brief.pdf — no extra information needed. If the PDF was available in a subdirectory inside projects called pdfs, the relative link would be pdfs/project-brief.pdf (the equivalent absolute URL would be <https://www.example.com/projects/pdfs/project-brief.pdf>.)

### Linking to non-HTML resources — leave clear signposts

When linking to a resource that will be downloaded (like a PDF or Word document), streamed (like video or audio), or has another potentially unexpected effect (opens a popup window), you should add clear wording to reduce any confusion.

For example:

If you're on a low bandwidth connection, click a link, and then a multiple megabyte download starts unexpectedly.
Let's look at some examples, to see what kind of text can be used here:

```HTML
<p>
  <a href="https://www.example.com/large-report.pdf">
    Download the sales report (PDF, 10MB)
  </a>
</p>

<p>
  <a href="https://www.example.com/video-stream/" target="_blank">
    Watch the video (stream opens in separate tab, HD quality)
  </a>
</p>
```

### Use the download attribute when linking to a download

When you are linking to a resource that's to be downloaded rather than opened in the browser, you can use the download attribute to provide a default save filename. Here's an example with a download link to the latest Windows version of Firefox:

```HTML
<a
  href="https://download.mozilla.org/?product=firefox-latest-ssl&os=win64&lang=en-US"
  download="firefox-latest-64bit-installer.exe">
  Download Latest Firefox for Windows (64-bit) (English, US)
</a>
```

## Email links

It's possible to create links or buttons that, when clicked, open a new outgoing email message rather than linking to a resource or page. This is done using the `<a>` element and the mailto: URL scheme.

In its most basic and commonly used form, a mailto: link indicates the email address of the intended recipient. For example:

```HTML
<a href="mailto:nowhere@mozilla.org">Send email to nowhere</a>
```

In fact, the email address is optional. If you omit it and your href is "mailto:", a new outgoing email window will be opened by the user's email client with no destination address. This is often useful as "Share" links that users can click to send an email to an address of their choosing.

### Specifying details

In addition to the email address, you can provide other information. In fact, any standard mail header fields can be added to the mailto URL you provide. The most commonly used of these are "subject", "cc", and "body" (which is not a true header field, but allows you to specify a short content message for the new email). Each field and its value is specified as a query term.

Here's an example that includes a cc, bcc, subject and body:

```HTML
<a
  href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&subject=The%20subject%20of%20the%20email&body=The%20body%20of%20the%20email">
  Send mail with cc, bcc, subject and body
</a>
```
