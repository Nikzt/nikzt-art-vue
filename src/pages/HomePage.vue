<template>
  <div>
    <NikztLogo class="noselect" />

    <splide :options="options">
      <splide-slide>
        <img src="../assets/gradient-portrait-1.png" />
      </splide-slide>
      <splide-slide>
        <img src="../assets/gradient-portrait-2.png" />
      </splide-slide>
      <splide-slide>
        <img src="../assets/sample-artwork-1.jpg" />
      </splide-slide>
      <splide-slide>
        <img src="../assets/sample-artwork-4.jpg" />
      </splide-slide>
      <splide-slide>
        <img src="../assets/sample-artwork-5.jpg" />
      </splide-slide>
    </splide>
  </div>
</template>

<script>
import "@splidejs/splide/dist/css/themes/splide-skyblue.min.css";
import NikztLogo from "../components/NikztLogo.vue";
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import {ref} from 'vue';

export default {
  name: "HomePage",
  components: { NikztLogo, Splide, SplideSlide },
  setup() {
    const options = ref({
      type: "loop",
      perPage: window.innerWidth > 750 ? 3 : 1,
      perMove: 1,
      focus: window.innerWidth > 750 ? "center" : 0,
      trimSpace: true,
      gap: "2.5rem",
      padding: {
        left: 0
      },
      lazyLoad: true,
      cover: true,
    });
    return { options };
  },
};
</script>

<style >
.logo {
  text-align: center;
}

.splide {
  margin-left: auto;
  margin-right: auto;
  width: 90%;
  max-width: 1080px;
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
  max-width: 20rem;
  min-width: 14rem;
  border-radius: 20px;
  height: 40vh;
  min-height: 400px;
}
img {
  height: 100%;
}
</style>