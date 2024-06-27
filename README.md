# svg-masked-video

SVG Mask(`<text>`) on a Video(`<video>`)

![preview](docs/preview.png)

### index.html
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="style.css" />
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap" rel="stylesheet">
  </head>
  <body>
    <video 
      xmlns="http://www.w3.org/1999/xhtml" 
      autoplay playsinline muted loop preload 
      poster="https://s3-us-west-2.amazonaws.com/s.cdpn.io/4273/oceanshot.jpg"
    >
      <source src="./skku.mp4" />
    </video>

    <svg viewBox="0 0 128 64" preserveAspectRatio="xMidYMid slice">
      <defs>
        <mask id="mask" x="0" y="0" width="100%" height="100%">
          <rect fill="white" x="0" y="0" width="100%" height="100%" />
          <text>SKKU</text>
        </mask>
      </defs>
      <rect fill="white" x="0" y="0" width="100%" height="100%" mask="url(#mask)" />
    </svg>
  </body>
  <script>
    // for video a11y
    const video = document.querySelector("video")
    if (window.matchMedia('(prefers-reduced-motion)').matches) {
      video.removeAttribute('autoplay');
      video.pause();
    }
  </script>
</html>
```

### style.css
```css
body {
  margin: 0;
  height: 100vh;
}

video {
  position: absolute;
  top: 50px;
  left: 50%;
  z-index: -1;
  width: 70vw;
  transform: translate(-50%, 0%);
}

svg {
  position: absolute;
  top: 50px;
  left: 0%;

  text {
    font-family: 'Poppins', sans-serif;
    font-weight: 900;
    font-size: 20pt;
    letter-spacing: -.1rem;
    text-transform: uppercase;
    transform: translate(22%, 60%);
  }
}
```

