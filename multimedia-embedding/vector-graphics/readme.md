# Adding vector graphics to the web

Vector graphics are very useful in many circumstances — they have small file sizes and are highly scalable, so they don't pixelate when zoomed in or blown up to a large size. In this article we'll show you how to include one in your webpage.

Learn how to embed an SVG (vector) image into a webpage.

## What are vector graphics?

On the web, you'll work with two types of images — raster images, and vector images:

- Raster images are defined using a grid of pixels — a raster image file contains information showing exactly where each pixel is to be placed, and exactly what color it should be. Popular web raster formats include Bitmap (.bmp), PNG (.png), JPEG (.jpg), and GIF (.gif.)
- Vector images are defined using algorithms — a vector image file contains shape and path definitions that the computer can use to work out what the image should look like when rendered on the screen. The SVG format allows us to create powerful vector graphics for use on the Web.

Moreover, vector image files are much lighter than their raster equivalents, because they only need to hold a handful of algorithms, rather than information on every pixel in the image individually.

## What is SVG?

SVG is an XML-based language for describing vector images. It's basically markup, like HTML, except that you've got many different elements for defining the shapes you want to appear in your image, and the effects you want to apply to those shapes. SVG is for marking up graphics, not content. SVG defines elements for creating basic shapes, like `<circle>` and `<rect>`, as well as elements for creating more complex shapes, like `<path>` and `<polygon>`. More advanced SVG features include `<feColorMatrix>` (transform colors using a transformation matrix), `<animate>` (animate parts of your vector graphic), and `<mask>` (apply a mask over the top of your image).

```HTML
<svg
  version="1.1"
  baseProfile="full"
  width="300"
  height="200"
  xmlns="http://www.w3.org/2000/svg">
  <rect width="100%" height="100%" fill="black" />
  <circle cx="150" cy="100" r="90" fill="blue" />
</svg>
```

From the example above, you may get the impression that SVG is easy to hand code. Yes, you can hand code simple SVG in a text editor, but for a complex image this quickly starts to get very difficult. For creating SVG images, most people use a vector graphics editor like `Inkscape` or `Illustrator`. These packages allow you to create a variety of illustrations using various graphics tools, and create approximations of photos (for example Inkscape's Trace Bitmap feature.)

SVG has some additional advantages besides those described so far:

- Text in vector images remains accessible (which also benefits your SEO).
- SVGs lend themselves well to styling/scripting, because each component of the image is an element that can be styled via CSS or scripted via JavaScript.

So why would anyone want to use raster graphics over SVG? Well, SVG does have some disadvantages:

- SVG can get complicated very quickly, meaning that file sizes can grow; complex SVGs can also take significant processing time in the browser.
- SVG can be harder to create than raster images, depending on what kind of image you are trying to create.

## Adding SVG to your pages

In this section we'll go through the different ways in which you can add SVG vector graphics to your web pages.

### The quick way: `<img/>` element

To embed an SVG via an `<img>` element, you just need to reference it in the src attribute as you'd expect. You will need a height or a width attribute (or both if your SVG has no inherent aspect ratio).

```HTML
<img
  src="equilateral.svg"
  alt="triangle with all three sides equal"
  height="87"
  width="100" />
```

Pros

- Quick, familiar image syntax with built-in text equivalent available in the alt attribute.
- You can make the image into a hyperlink easily by nesting the `<img>` inside an `<a>` element.
- The SVG file can be cached by the browser, resulting in faster loading times for any page that uses the image loaded in the future.

Cons

- You cannot manipulate the image with JavaScript.
- If you want to control the SVG content with CSS, you must include inline CSS styles in your SVG code. (External stylesheets invoked from the SVG file take no effect.)
- You cannot restyle the image with CSS pseudoclasses (like :focus).

### How to include SVG code inside your HTML

You can also open up the SVG file in a text editor, copy the SVG code, and paste it into your HTML document — this is sometimes called putting your SVG inline, or inlining SVG. Make sure your SVG code snippet begins with an `<svg>` start tag and ends with an `</svg>` end tag. Here's a very simple example of what you might paste into your document:

```HTML
<svg width="300" height="200">
  <rect width="100%" height="100%" fill="green" />
</svg>
```

Pros

- Putting your SVG inline saves an HTTP request, and therefore can reduce your loading time a bit.
- You can assign classes and ids to SVG elements and style them with CSS, either within the SVG or wherever you put the CSS style rules for your HTML document. In fact, you can use any SVG presentation attribute as a CSS property.
- Inlining SVG is the only approach that lets you use CSS interactions (like `:focus`) and CSS animations on your SVG image (even in your regular stylesheet.)
- You can make SVG markup into a hyperlink by wrapping it in an `<a>` element.

Cons

- This method is only suitable if you're using the SVG in only one place. Duplication makes for resource-intensive maintenance.
- Extra SVG code increases the size of your HTML file.
- The browser cannot cache inline SVG as it would cache regular image assets, so pages that include the image will not load faster after the first page containing the image is loaded.
- You may include fallback in a `<foreignObject>` element, but browsers that support SVG still download any fallback images. You need to weigh whether the extra overhead is really worthwhile, just to support obsolescent browsers.

### How to embed an SVG with an iframe

You can open SVG images in your browser just like webpages.

```HTML
<iframe src="triangle.svg" width="500" height="500" sandbox>
  <img src="triangle.png" alt="Triangle with three unequal sides" />
</iframe>
```

This is definitely not the best method to choose:

Cons

- iframes do have a fallback mechanism, as you can see, but browsers only display the fallback if they lack support for iframes altogether.
- Moreover, unless the SVG and your current webpage have the same origin, you cannot use JavaScript on your main webpage to manipulate the SVG.
