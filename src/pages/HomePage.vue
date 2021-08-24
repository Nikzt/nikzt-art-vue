<template>
  <div>
    <NikztLogo class="noselect"/>
    <div class="sample-gallery">
      <img src="../assets/sample-artwork-1.jpg" />
      <img src="../assets/sample-artwork-2.jpg" />
      <img src="../assets/sample-artwork-3.jpg" />
      <img src="../assets/sample-artwork-4.jpg" />
      <img src="../assets/sample-artwork-5.jpg" />
      <img src="../assets/sample-artwork-6.jpg" />
    </div>
  </div>
</template>

<script>
import NikztLogo from "../components/NikztLogo.vue";

export default {
  name: "HomePage",
  components: { NikztLogo },
};
</script>

<style scoped>
.sample-gallery {
  display: flex;
  flex-wrap: wrap;
  align-content: space-around;
}
img {
  margin: 20px;
  border-radius: 20px;
  display: block;
  height: 30vh;
}
</style>