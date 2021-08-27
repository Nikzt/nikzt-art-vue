<template>
  <div v-if="showPreview" id="image-preview">
      <img :src="imageUrl" />
  </div>
</template>

<script>
export default {
  name: "ImagePreview",
  props: {
    imageUrl: String,
    showPreview: Boolean,
  },
};
</script>

<style scoped>
#image-preview {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(56, 5, 77, 0.315);
  z-index: 200;
  display: flex;
  align-items: center;
  justify-content: center;
}

img {
  max-width: 800px;
  max-height: 800px;
}

@media screen and (max-width: 750px) {
  img {
    max-width: 90%;
  }
}

@media screen and (max-width: 500px) {
  img {
    max-width: 100%;
  }
}

img {
  border-radius: 20px;
  width: 100%;
  max-height: 90vh;
  object-fit: cover;
  box-shadow: 0 0 20px black;
}
</style>