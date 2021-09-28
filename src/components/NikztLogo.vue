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

/* Fluid typography: scale size of text with screen width below this threshold */
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
  background-image: linear-gradient(
    140deg,
    var(--color-gradient-start) 0%,
    var(--color-gradient-end) 100%
  );
  transition: opacity 0.3s ease-in-out;
}

/* The parent theme class determines which gradient 'art' text to show */

.hot.gradient-art {
  opacity: 0;
}

.theme-hot .hot.gradient-art {
  opacity: 1;
}

.purple.gradient-art {
  opacity: 0;
}

.theme-cool-purple .purple.gradient-art {
  opacity: 1;
}

.aurora.gradient-art {
  opacity: 0;
}

.theme-aurora .aurora.gradient-art {
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