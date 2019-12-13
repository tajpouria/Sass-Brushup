## Introduction to responsive images

### Responsive images in html

The goal of responsive images is to serve the right image for to right screen size in order to avoid from downloading unnecessary downloading large images on smaller screens.

In responsive images subject there is three concepts that make sense:

- **Resolution switching**: decrease image resolution on smaller screens

```html
<img
  srcset="image/nat-small.jpg 300w, image/nat-large.jpg 1000w"
  sizes="(max-width: 900px) 20vw, (max-width: 600px) 30vw, 300px"
  src="image/nat-large.jpg"
/>
```

_`300w` and `1000w` are width descriptors and define the image width - specify `src` in cases that browser does not support_

- **Density switching**: half the image resolution on @1x screens

```html
<img srcset="img/logo-1x.png 1x, img/logo-2x.png 2x" src="img/logo-1x.png" />
```

_`1x` and `2x` is density descriptor_

- **Art direction**: different images on different screen sizes

```html
<picture>
  <source
    srcset="img/logo-small-1x.png 1x, img/logo-small-2x.png 2x"
    media="(max-width: 37.5em)"
    src="img/logo-small-1x.png"
  />
  <img
    srcset="img/logo-1x.png 1x, img/logo-2x.png 2x"
    src="img/logo-small-1x.png"
  />
</picture>
```

### Responsive images in css

```scss
// target resolution by min-resolution media query 192 dot per inches are actually instance for 2x screen resolution also -webkit-min-device-pixel-ratio added in order to support on safari
@media (min-resolution: 192dpi) and (min-width: 37.5em),
  (-webkit-min-device-pixel-ratio: 2) and (min-width: 37.5em),
  (min-width: 125em) {
  background-image: url(images/big-image.jpg);
}
```
