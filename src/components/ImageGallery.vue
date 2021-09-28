<template>
  <splide
    :options="options"
    @splide:click="onSlideClick"
    @splide:active="onSlideActive"
  >
    <splide-slide v-for="image in images" v-bind:key="image.url">
      <div class="box-shadow-area"></div>
      <div class="box-shadow-area-2"></div>
      <img :src="`${image.url}`" />
    </splide-slide>
  </splide>
</template>

<script>
import "@splidejs/splide/dist/css/themes/splide-skyblue.min.css";
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import { ref } from "vue";

export default {
  name: "ImageGallery",
  components: { Splide, SplideSlide },
  props: {
    images: Array,
    onChangeTheme: Function,
  },
  setup(props) {
    const options = {
      type: "slide",
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
        bottom: 20,
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
    };

    return {
      options,
      selectedImageUrl,
      onSlideClick,
      onSlideActive,
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

.splide__arrow svg {
  fill: var(--color-primary);
}

.splide__arrow svg:hover {
  fill: var(--color-primary-light);
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
  filter: grayscale(100%);
  transition: filter 0.3s ease-in-out;
}

.splide__slide.is-active {
  filter: none;
}

.splide__slide.is-active .box-shadow-area,
.box-shadow-area-2 {
  width: 100%;
  height: 100%;
  border-radius: 20px;
  position: absolute;
  transition: box-shadow 0.3s ease-in-out;
}

.splide__slide.is-active .box-shadow-area {
  box-shadow: 0px 0px 20px var(--color-primary);
}
.splide__slide.is-active .box-shadow-area-2 {
  box-shadow: 0px 0px 10px var(--color-primary-light);
}

.splide__arrow {
  visibility: hidden;
}

@media screen and (max-width: 750px) {
    .splide__arrow {
      visibility: visible;
    }
}

img {
  height: 100%;
}
</style>