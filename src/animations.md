---
layout: base.njk
title: Animations
permalink: /animations/
---

<div class="animation-stage" aria-label="Random color animation">
  <canvas class="animation-circle animation-circle--pixels" id="pixel-circle" width="160" height="160" role="img" aria-label="A circle of pixels changing to random colors at independent intervals"></canvas>
</div>

<script>
  (() => {
    const pixelCircle = document.getElementById("pixel-circle");
    const context = pixelCircle.getContext("2d", { alpha: false });
    const image = context.createImageData(pixelCircle.width, pixelCircle.height);
    const pixelCount = pixelCircle.width * pixelCircle.height;
    const nextChange = new Float64Array(pixelCount);
    const maximumDelay = 10000;

    function randomizePixel(pixelIndex) {
      const pixels = image.data;
      const dataIndex = pixelIndex * 4;

      pixels[dataIndex] = Math.floor(Math.random() * 256);
      pixels[dataIndex + 1] = Math.floor(Math.random() * 256);
      pixels[dataIndex + 2] = Math.floor(Math.random() * 256);
      pixels[dataIndex + 3] = 255;
    }

    for (let pixelIndex = 0; pixelIndex < pixelCount; pixelIndex += 1) {
      randomizePixel(pixelIndex);
      nextChange[pixelIndex] = Math.random() * maximumDelay;
    }

    function animate(timestamp) {
      for (let pixelIndex = 0; pixelIndex < pixelCount; pixelIndex += 1) {
        if (timestamp >= nextChange[pixelIndex]) {
          randomizePixel(pixelIndex);
          nextChange[pixelIndex] = timestamp + Math.random() * maximumDelay;
        }
      }

      context.putImageData(image, 0, 0);
      window.requestAnimationFrame(animate);
    }

    window.requestAnimationFrame(animate);
  })();
</script>
