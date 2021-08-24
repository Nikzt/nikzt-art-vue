<template>
  <div class="logo">
    <h2 class="nikzt-title">nikzt.</h2>
    <h2 class="gradient-art" data-text="art">art</h2>
  </div>
</template>

<script>
export default {
  name: "NikztLogo",
};
</script>

<style scoped>
h2 {
  display: inline;
  color: rgb(240, 227, 244);
  font-weight: 200;
  font-size: 4em;
}

.logo {
  margin-bottom: 20px;
}

.gradient-art {
  display: inline;
  font-weight: 400;
  background-image: linear-gradient(
    140deg,
    rgb(223, 64, 46) 0%,
    rgb(106, 29, 182) 100%
  );
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.gradient-art:before {
  content: attr(data-text);
  position: absolute;
  z-index: -1;
}
</style>