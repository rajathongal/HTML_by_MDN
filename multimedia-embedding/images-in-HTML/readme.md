# Images in HTML

## How do we put an image on a webpage?

In order to put a simple image on a web page, we use the `<img>` element. This is a void element (meaning, it cannot have any child content and cannot have an end tag) that requires two attributes to be useful: `src` and `alt`. The `src` attribute contains a URL pointing to the image you want to embed in the page. As with the `href` attribute for `<a>` elements, the `src` attribute can be a relative URL or an absolute URL. Without a `src` attribute, an img element has no image to load.

```HTML
<!-- Example usage -->
<img src="dinosaur.jpg" alt="Dinosaur" />
<img src="images/dinosaur.jpg" alt="Dinosaur" />
<img src="https://www.example.com/images/dinosaur.jpg" alt="Dinosaur" />
```

Linking via absolute URLs is not recommended, however. You should host the images you want to use on your site, which in simple setups means keeping the images for your website on the same server as your HTML. In addition, it is more efficient to use relative URLs than absolute URLs in terms of maintenance (when you move your site to a different domain, you won't need to update all your URLs to include the new domain). In more advanced setups, you might use a `CDN (Content Delivery Network)` to deliver your images.

### Alternative text

The next attribute we'll look at is alt. Its value is supposed to be a textual description of the image, for use in situations where the image cannot be seen/displayed or takes a long time to render because of a slow internet connection. For example, our above code could be modified like so:

```HTML
<img
  src="images/dinosaur.jpg"
  alt="The head and torso of a dinosaur skeleton;
          it has a large head with long sharp teeth" />
```

### Width and height

You can use the width and height attributes to specify the width and height of your image. They are given as integers without a unit, and represent the image's width and height in pixels.

```HTML
<img
  src="images/dinosaur.jpg"
  alt="The head and torso of a dinosaur skeleton;
          it has a large head with long sharp teeth"
  width="400"
  height="341" />
```

```HTML
<h1>Images in HTML</h1>

<img
  src="dinosaur.jpg"
  alt="The head and torso of a dinosaur skeleton; it has a large head with long sharp teeth"
  title="A T-Rex on display in the Manchester University Museum" />
<blockquote>
  <p>
    But down there it would be dark now, and not the lovely lighted aquarium she
    imagined it to be during the daylight hours, eddying with schools of tiny,
    delicate animals floating and dancing slowly to their own serene currents
    and creating the look of a living painting. That was wrong, in any case. The
    ocean was different from an aquarium, which was an artificial environment.
    The ocean was a world. And a world is not art. Dorothy thought about the
    living things that moved in that world: large, ruthless and hungry. Like us
    up here.
  </p>
  <footer>- Rachel Ingalls, <cite>Mrs. Caliban</cite></footer>
</blockquote>
```

### Image titles

As with links, you can also add title attributes to images, to provide further supporting information if needed. In our example, we could do this:

```HTML
<img
  src="images/dinosaur.jpg"
  alt="The head and torso of a dinosaur skeleton;
          it has a large head with long sharp teeth"
  width="400"
  height="341"
  title="A T-Rex on display in the Manchester University Museum" />
```

### Annotating images with figures and figure captions

Speaking of captions, there are a number of ways that you could add a caption to go with your image. For example, there would be nothing to stop you from doing this:

```HTML
<div class="figure">
  <img
    src="images/dinosaur.jpg"
    alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
    width="400"
    height="341" />

  <p>A T-Rex on display in the Manchester University Museum.</p>
</div>
```

A better solution, is to use the HTML `<figure>` and `<figcaption>` elements. These are created for exactly this purpose: to provide a semantic container for figures, and to clearly link the figure to the caption. Our above example could be rewritten like this:

```HTML
<figure>
  <img
    src="images/dinosaur.jpg"
    alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
    width="400"
    height="341" />

  <figcaption>
    A T-Rex on display in the Manchester University Museum.
  </figcaption>
</figure>
```

The `<figcaption>` element tells browsers, and assistive technology that the caption describes the other content of the `<figure>` element.

A figure doesn't have to be an image. It is an independent unit of content that:

- Expresses your meaning in a compact, easy-to-grasp way.
- Could go in several places in the page's linear flow.
- Provides essential information supporting the main text.

A figure could be several images, a code snippet, audio, video, equations, a table, or something else.

### CSS background images

You can also use CSS to embed images into webpages (and JavaScript, but that's another story entirely). The CSS background-image property, and the other background-* properties, are used to control background image placement. For example, to place a background image on every paragraph on a page, you could do this:

```CSS
p {
  background-image: url("images/dinosaur.jpg");
}
```

The resulting embedded image is arguably easier to position and control than HTML images. So why bother with HTML images? As hinted to above, CSS background images are for decoration only. If you just want to add something pretty to your page to enhance the visuals, this is fine. Though, such images have no semantic meaning at all. They can't have any text equivalents, are invisible to screen readers, and so on. This is where HTML images shine!

### Other graphics on the web

We've seen that static images can be displayed using the `<img>` element, or by setting the background of HTML elements using the background-image property. You can also construct graphics on-the-fly, or manipulate images after the fact. The browser offers ways of creating 2D and 3D graphics with code, as well as including video from uploaded files or live streamed from a user's camera. Here are links to articles that provide insight into these more advanced graphics topics:

- Canvas

The `<canvas>` element provides APIs to draw 2D graphics using JavaScript.

- SVG

Scalable Vector Graphics (SVG) lets you use lines, curves, and other geometric shapes to render 2D graphics. With vectors, you can create images that scale cleanly to any size.

- WebGL

The WebGL API guide will get your started with WebGL, the 3D graphics API for the Web that lets you use standard OpenGL ES in web content.

- Using HTML audio and video

Just like `<img>`, you can use HTML to embed `<video>` and `<audio`> into a web page and control its playback.

- WebRTC

The RTC in WebRTC stands for Real-Time Communications, a technology that enables audio/video streaming and data sharing between browser clients (peers).
