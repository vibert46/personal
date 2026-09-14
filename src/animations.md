---
layout: base.njk
title: Animations
permalink: /animations/
---

<div class="animation-stage" aria-label="Two color animations">
  <div class="animation-circle animation-circle--binary" id="binary-circle" role="img" aria-label="A circle alternating between black and white"></div>
  <canvas class="animation-circle animation-circle--pixels" id="pixel-circle" width="72" height="72" role="img" aria-label="A circle of pixels changing to random colors"></canvas>
</div>

<script>
  (() => {
    const binaryCircle = document.getElementById("binary-circle");
    const pixelCircle = document.getElementById("pixel-circle");
    const context = pixelCircle.getContext("2d", { alpha: false });
    const image = context.createImageData(pixelCircle.width, pixelCircle.height);
    let isWhite = false;

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

    function updateAnimations() {
      isWhite = !isWhite;
      binaryCircle.style.backgroundColor = isWhite ? "#fff" : "#000";
      randomizePixels();
    }

    randomizePixels();
    window.setInterval(updateAnimations, 1000);
  })();
</script>
