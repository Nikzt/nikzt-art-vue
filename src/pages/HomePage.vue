<template>
  <div>
    <NikztLogo class="noselect" />

    <splide :options="options">
      <splide-slide>
        <img src="../assets/gradient-portrait-1.png" />
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
import { computed, onMounted, onUnmounted, ref } from "vue";

export default {
  name: "HomePage",
  components: { NikztLogo, Splide, SplideSlide },
  setup() {
    const windowWidth = ref(window.innerWidth);
    const onWidthChange = () => (windowWidth.value = window.innerWidth);
    onMounted(() => window.addEventListener("resize", onWidthChange));
    onUnmounted(() => window.removeEventListener("resize", onWidthChange));
    const options = computed(() => {
      console.log(windowWidth.value)
      return {
        type: "loop",
        height: "40vh",
        fixedHeight: "35vh",
        rewind: true,
        perPage: windowWidth.value > 1200 ? 3 : 1,
        perMove: 1,
        focus: "center",
        trimSpace: true,
        gap: "5em",
      };
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
  max-width: 1080px;
}
.sample-gallery {
  display: flex;
  flex-wrap: wrap;
  align-content: space-around;
}

.splide__track {
  width: 90%;
  margin: 0 auto 0 auto;
  border-radius: 20px;
}

.splide__pagination {
  bottom: -2em;
}
img {
  display: block;
  margin-left: auto;
  margin-right: auto;
  border-radius: 20px;
  height: 100%;
  max-width: 20rem;
  object-fit: cover;
}
</style>