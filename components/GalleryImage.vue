<template lang="html">
  <!--<img class="a-galleryImage" :src="imgSrc" alt="No Image">-->
  <figure>
    <div
    class="a-galleryImage"
    :style="'background-image: url('+imgSrc+');'">
    </div>
    <figcaption class="a-galleryImage__caption">Placeholder</figcaption>
  </figure>
</template>

<script>
export default {
  props: {
    "imgSrc": String
  }
}
</script>

<style lang="css">
  .a-galleryImage {
    width: 375px;
    height: 375px;

    background-size: cover;
  }

  .a-galleryImage__caption {
    font-weight: 100;
    text-transform: uppercase;
    text-align: center;

    padding: 10px;
    letter-spacing: 1.5px;
  }
</style>
