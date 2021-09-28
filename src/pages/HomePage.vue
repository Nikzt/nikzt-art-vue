<template>
  <div id="home-page" :class="selectedTheme">
    <NikztLogo class="noselect" />

    <ImageGallery :images="images" :onChangeTheme="onChangeTheme" />
  </div>
</template>

<script>
import NikztLogo from "../components/NikztLogo.vue";
import ImageGallery from "../components/ImageGallery.vue";
import { ref } from "vue";

export default {
  name: "HomePage",
  components: { NikztLogo, ImageGallery },
  setup() {
    const selectedTheme = ref("theme-hot");

    /** Contains image URLs and their associate color scheme */
    const images = [
      {
        url: require("../images/gradient-portrait-hot.jpg"),
        themeClass: "theme-hot",
        colorBackground: "rgb(34, 7, 19)",
        colorGradientStart: "rgb(230, 62, 44)",
        colorGradientEnd: "rgb(209, 6, 141)",
        colorPrimary: "rgb(235, 77, 132)",
        colorPrimaryLight: "rgb(238, 142, 164)",
      },
      {
        url: require("../images/gradient-portrait-cool-purple.jpg"),
        themeClass: "theme-cool-purple",
        colorBackground: "rgb(34, 3, 48)",
        colorGradientStart: "rgb(222, 89, 240)",
        colorGradientEnd: "rgb(25, 72, 228)",
        colorPrimary: "rgb(186, 144, 245)",
        colorPrimaryLight: "rgb(217, 194, 255)",
      },
      {
        url: require("../images/gradient-portrait-aurora.jpg"),
        themeClass: "theme-aurora",
        colorBackground: "#161329",
        colorGradientStart: "rgb(38, 228, 241)",
        colorGradientEnd: "rgb(0, 163, 95)",
        colorPrimary: "rgb(118, 255, 246)",
        colorPrimaryLight: "rgb(175, 255, 250)",
      },
    ];

    /** 
     * Sets the CSS variables of the root element for the selected theme.
     * @param themeString The CSS class name used to identify the theme
     */
    const onChangeTheme = (themeString) => {
      selectedTheme.value = themeString;
      const imageTheme = images.find(i => i.themeClass === themeString);

      document.documentElement.className = themeString;
      document.documentElement.style.setProperty("--color-background", imageTheme.colorBackground);
      document.documentElement.style.setProperty("--color-gradient-start", imageTheme.colorGradientStart);
      document.documentElement.style.setProperty("--color-gradient-end", imageTheme.colorGradientEnd);
      document.documentElement.style.setProperty("--color-primary", imageTheme.colorPrimary);
      document.documentElement.style.setProperty("--color-primary-light", imageTheme.colorPrimaryLight);
    };

    return { images, selectedTheme, onChangeTheme };
  },
};
</script>

<style >
.logo {
  padding-top: 30px;
}
#home-page {
  width: 100%;
  height: 100%;
  background-color: transparent;
}
</style>