<template lang="html">
  <section id="m-gallery" class="m-gallery">
    <a-galleryImage
    v-for="image in images"
    :key="image.id"
    :imgSrc="'https://picsum.photos/400/' + size + '/?image=' + image.id ">
  </a-galleryImage>
  </section>
</template>

<script>
import GalleryImage from "~/components/GalleryImage.vue"
import fetch from 'node-fetch'

//https://api.unsplash.com/photos/?client_id="+this.client_id

export default {
  name: 'm-gallery',
  components: {
    'a-galleryImage': GalleryImage
  },

  data() {
    return{
      images: [],
      size: "400",
      limit: 9
    }
  },

  created() {
    this.fetchImages()
  },

  methods: {
    fetchImages() {
      fetch("https://picsum.photos/list")
      .then((resp) => resp.json())
      .then((data) => {
        var start = 50;
        this.images = data.slice(start, start+this.limit)
      })
    }
  }
}
</script>

<style lang="css">
  .m-gallery {
    display: grid;
    grid-template-columns: auto auto auto;
    place-items: center;
    place-content: center;

    grid-column-gap: 40px;
    grid-row-gap: 40px;

    width: 90%;
    margin-left: auto;
    margin-right: auto;
  }
</style>
