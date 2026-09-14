---
layout: base.njk
title: Animations
permalink: /animations/
---

<div class="animation-stage" aria-label="Random color animation">
  <canvas class="animation-circle animation-circle--pixels" id="pixel-circle" width="72" height="72" role="img" aria-label="A circle of pixels changing to random colors"></canvas>
</div>

<script>
  (() => {
    const pixelCircle = document.getElementById("pixel-circle");
    const context = pixelCircle.getContext("2d", { alpha: false });
    const image = context.createImageData(pixelCircle.width, pixelCircle.height);

    function randomizePixels() {
      const pixels = image.data;

      for (let index = 0; index < pixels.length; index += 4) {
        pixels[index] = Math.floor(Math.random() * 256);
        pixels[index + 1] = Math.floor(Math.random() * 256);
        pixels[index + 2] = Math.floor(Math.random() * 256);
        pixels[index + 3] = 255;
      }

      context.putImageData(image, 0, 0);
    }

    randomizePixels();
    window.setInterval(randomizePixels, 1000);
  })();
</script>
