<template>
  <splide :options="options" @splide:click="onSlideClick" @splide:active="onSlideActive">
    <splide-slide v-for="image in images" v-bind:key="image.url">
      <div class="box-shadow-area"></div>
      <div class="box-shadow-area-2"></div>
      <img :src="`${image.url}`" />
    </splide-slide>
  </splide>
  <image-preview
    :showPreview="showPreview"
    :imageUrl="selectedImageUrl"
    @click="onPreviewClick"
  />
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
    images: Array,
    onChangeTheme: Function
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
      updateOnMove: true,
      pagination: false,
      cover: true,
      slideFocus: true,
      padding: {
        left: 20,
        right: 20,
        top: 20,
        bottom: 20
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
      splide.go(slide.index);
    };

    const onSlideActive = (splide, slide) => {
      const idx =
        slide.index >= 0 && slide.index < props.images.length
          ? slide.index
          : slide.realIndex;
      const themeClass = props.images[idx].themeClass;
      props.onChangeTheme(themeClass);
    }

    const onPreviewClick = () => {
      showPreview.value = false;
    };

    return {
      options,
      showPreview,
      selectedImageUrl,
      onSlideClick,
      onPreviewClick,
      onSlideActive
    };
  },
};
</script>

<style>
.splide {
  margin-left: auto;
  margin-right: auto;
  width: 75vw;
  max-width: 860px;
  height: 40vh;
  min-height: 400px;
}

.splide__track {
  margin: 0 auto 0 auto;
  border-radius: 20px;
  padding: 20px 0 20px 0;
}

.splide__arrow--next {
  right: -3em;
}

.splide__arrow--prev {
  left: -3em;
}

.theme-aurora .splide__arrow svg {
  fill: rgb(118, 255, 246);
}

.theme-aurora .splide__arrow svg:hover {
  fill: rgb(175, 255, 250);
}

.theme-cool-purple .splide__arrow svg {
  fill: rgb(186, 144, 245);
}

.theme-cool-purple .splide__arrow svg:hover {
  fill: rgb(217, 194, 255);
}

.theme-hot .splide__arrow svg {
  fill: rgb(235, 77, 132);
}

.theme-hot .splide__arrow svg:hover {
  fill: rgb(238, 142, 164);
}

.splide__pagination {
  bottom: -2em;
}

.splide__slide {
  max-width: 30rem;
  border-radius: 20px;
  height: 40vh;
  min-height: 400px;
  cursor: pointer;
}

.splide__slide.is-active .box-shadow-area, .box-shadow-area-2 {
  width: 100%;
  height: 100%;
  border-radius: 20px;
  position: absolute;
  transition: box-shadow 0.2s linear;
}


.theme-hot .splide__slide.is-active .box-shadow-area {
  box-shadow: 0px 0px 20px rgb(245, 24, 90);
}
.theme-hot .splide__slide.is-active .box-shadow-area-2 {
  box-shadow: 0px 0px 10px rgb(255, 120, 96);
}

.theme-aurora .splide__slide.is-active .box-shadow-area {
  box-shadow: 0px 0px 20px rgb(41, 228, 241);
}
.theme-aurora .splide__slide.is-active .box-shadow-area-2 {
  box-shadow: 0px 0px 10px rgba(255, 255, 255, 0.808);
}

.theme-cool-purple .splide__slide.is-active .box-shadow-area {
  box-shadow: 0px 0px 20px rgb(44, 25, 214);
}
.theme-cool-purple .splide__slide.is-active .box-shadow-area-2 {
  box-shadow: 0px 0px 10px rgba(230, 128, 255, 0.836);
}

.splide__slide:hover {
}
img {
  height: 100%;
}
</style>