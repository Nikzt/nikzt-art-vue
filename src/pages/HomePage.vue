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
    const images = [
      {
        url: require("../images/gradient-portrait-hot.jpg"),
        themeClass: "theme-hot",
        primaryColor: "#e63e2c",
      },
      {
        url: require("../images/gradient-portrait-cool-purple.jpg"),
        themeClass: "theme-cool-purple",
        primaryColor: "",
      },
      {
        url: require("../images/gradient-portrait-aurora.jpg"),
        themeClass: "theme-aurora",
        primaryColor: "",
      },
    ];

    const onChangeTheme = (themeString) => {
      selectedTheme.value = themeString;
      document.documentElement.className = themeString;
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
}

.theme-hot {
  background-color: rgb(34, 7, 19);
  transition: background-color 0.3s linear;
}
.theme-cool-purple {
  background-color: rgb(34, 3, 48);
  transition: background-color 0.3s linear;
}
.theme-aurora {
  background-color: #161329;
  transition: background-color 0.3s linear;
}
</style>