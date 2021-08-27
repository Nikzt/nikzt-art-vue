<template>
  <splide :options="options" @splide:click="onSlideClick">
    <splide-slide v-for="url in imageUrls" v-bind:key="url">
      <img :src="`${url}`" />
    </splide-slide>
  </splide>
  <image-preview :showPreview="showPreview" :imageUrl="selectedImageUrl" @click="onPreviewClick" />
</template>

<script>
import "@splidejs/splide/dist/css/themes/splide-skyblue.min.css";
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import ImagePreview from "./ImagePreview.vue";
import { ref } from "vue";

export default {
  name: "ImageGallery",
  components: { Splide, SplideSlide, ImagePreview },
  props: {
    imageUrls: Array,
  },
  setup(props) {
    const options = {
      type: "loop",
      perPage: 3,
      perMove: 1,
      focus: "center",
      trimSpace: true,
      gap: "2.5rem",
      lazyLoad: true,
      cover: true,
      slideFocus: true,
      padding: {
        left: 0,
      },
      breakpoints: {
        750: {
          perPage: 2,
          focus: 0,
        },
        500: {
          perPage: 1,
          focus: 0,
        },
      },
    };

    const showPreview = ref(false);
    const selectedImageUrl = ref("");

    const onSlideClick = (splide, slide) => {
      showPreview.value = true;
      const idx =
        slide.index >= 0 && slide.index < props.imageUrls.length
          ? slide.index
          : slide.realIndex;
      selectedImageUrl.value = props.imageUrls[idx];
    };

    const onPreviewClick = () => {
      showPreview.value = false;
    }

    return {
      options,
      showPreview,
      selectedImageUrl,
      onSlideClick,
      onPreviewClick
    };
  },
};
</script>

<style>
.splide {
  margin-left: auto;
  margin-right: auto;
  width: 90%;
  max-width: 860px;
  height: 40vh;
  min-height: 400px;
}

.splide__track {
  margin: 0 auto 0 auto;
  border-radius: 20px;
}

.splide__arrow--next {
  right: -3em;
}

.splide__arrow--prev {
  left: -3em;
}

.splide__pagination {
  bottom: -2em;
}

.splide__slide {
  max-width: 30rem;
  min-width: 14rem;
  border-radius: 20px;
  height: 40vh;
  min-height: 400px;
  cursor: pointer;
  transition: opacity 0.08s linear;
}

.splide__slide:hover {
  opacity: 0.8;
  transition: opacity 0.08s linear;
}
img {
  height: 100%;
}
</style>