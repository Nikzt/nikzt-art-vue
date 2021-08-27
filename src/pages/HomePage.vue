<template>
  <div>
    <NikztLogo class="noselect" />

    <ImageGallery :imageUrls="imageUrls"/>
  </div>
</template>

<script>
import NikztLogo from "../components/NikztLogo.vue";
import ImageGallery from "../components/ImageGallery.vue";

export default {
  name: "HomePage",
  components: { NikztLogo, ImageGallery },
  setup() {

    const imageUrls = [
      require("../images/gradient-portrait-1.jpg"),
      require("../images/gradient-portrait-2.jpg"),
      require("../images/sample-artwork-1.jpg"),
      require("../images/sample-artwork-2.jpg"),
      require("../images/sample-artwork-3.jpg"),
      require("../images/gradient-portrait-3.jpg"),
    ]

    return { imageUrls };
  },
};
</script>

<style >
</style>