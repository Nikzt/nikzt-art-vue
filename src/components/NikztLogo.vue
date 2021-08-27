<template>
  <div class="logo-container">
    <div class="logo">
      <h2 class="nikzt-title">nikzt.</h2>
      <h2 class="placeholder-text">art</h2>
      <h2 class="gradient-art hot" data-text="art">art</h2>
      <h2 class="gradient-art purple" data-text="art">art</h2>
      <h2 class="gradient-art aurora" data-text="art">art</h2>
    </div>
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

@media screen and (max-width: 400px) {
  h2 {
    font-size: calc(64px + (64 - 32) * ((100vw - 400px) / (200)));
  }
}

.logo-container {
  display: flex;
  align-content: center;
  justify-content: center;
}

.logo {
  position: relative;
  margin-bottom: 20px;
  text-align: center;
}

.gradient-art {
  display: inline;
  position: absolute;
  margin: 0;
  right: 0;
  font-weight: 400;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.hot.gradient-art {
  background-image: linear-gradient(
    140deg,
    rgb(230, 62, 44) 0%,
    rgb(209, 6, 141) 100%
  );
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
}

.theme-hot .hot.gradient-art {
  transition: opacity 0.3s ease-in-out;
  opacity: 1;
}

.purple.gradient-art {
  background-image: linear-gradient(
    140deg,
    rgb(222, 89, 240) 0%,
    rgb(25, 72, 228) 100%
  );
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
}

.theme-cool-purple .purple.gradient-art {
  opacity: 1;
  transition: opacity 0.3s ease-in-out;
}

.aurora.gradient-art {
  background-image: linear-gradient(
    140deg,
    rgb(38, 228, 241) 0%,
    rgb(0, 163, 95) 100%
  );
  opacity: 0;
  transition: opacity 0.3s ease-in-out;
}

.theme-aurora .aurora.gradient-art {
  transition: opacity 0.3s ease-in-out;
  opacity: 1;
}

.gradient-art:before {
  content: attr(data-text);
  position: absolute;
  z-index: -1;
}

.placeholder-text {
  visibility: hidden;
}
</style>