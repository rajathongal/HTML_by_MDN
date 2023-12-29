# Iframe and other embedding technologies

Now, Looking at some elements that allow you to embed a wide variety of content types into your webpages: the `<iframe>`, `<embed>` and `<object>` elements. `<iframe>`s are for embedding other web pages, and the other two allow you to embed external resources such as PDF files.

```HTML
<iframe
    src="https://developer.mozilla.org/en-US/docs/Glossary"
    width="100%"
    height="500"
    allowfullscreen
    sandbox
>
    <p>
    <a href="/en-US/docs/Glossary">
        Fallback link for browsers that don't support iframes
    </a>
    </p>
</iframe>
```

## Always use the sandbox attribute

You want to give attackers as little power as you can to do bad things on your website, therefore you should give embedded content only the permissions needed for doing its job. Of course, this applies to your own content, too. A container for code where it can be used appropriately — or for testing — but can't cause any harm to the rest of the codebase (either accidental or malicious) is called a sandbox.

Content that's not sandboxed may be able to execute JavaScript, submit forms, trigger popup windows, etc. By default, you should impose all available restrictions by using the sandbox attribute with no parameters, as shown in our previous example.

If absolutely required, you can add permissions back one by one (inside the sandbox="" attribute value) — see the sandbox reference entry for all the available options. One important note is that you should never add both allow-scripts and allow-same-origin to your sandbox attribute — in that case, the embedded content could bypass the Same-origin policy that stops sites from executing scripts, and use JavaScript to turn off sandboxing altogether.

## Configure CSP directives

CSP stands for content security policy and provides a set of HTTP Headers (metadata sent along with your web pages when they are served from a web server) designed to improve the security of your HTML document. When it comes to securing `<iframe>`s, you can configure your server to send an appropriate X-Frame-Options header. This can prevent other websites from embedding your content in their web pages (which would enable clickjacking and a host of other attacks), which is exactly what the MDN developers have done, as we saw earlier on.

## The `<embed>` and `<object>` elements

The `<embed>` and `<object>` elements serve a different function to `<iframe>` — these elements are general purpose embedding tools for embedding external content, such as PDFs.

However, you are unlikely to use these elements very much. If you need to display PDFs, it's usually better to link to them, rather than embedding them in the page.

Historically these elements have also been used for embedding content handled by browser plugins such as Adobe Flash, but this technology is now obsolete and is not supported by modern browsers.

```HTML
<object data="mypdf.pdf" type="application/pdf" width="800" height="1200">
  <p>
    You don't have a PDF plugin, but you can
    <a href="mypdf.pdf">download the PDF file. </a>
  </p>
</object>
```
