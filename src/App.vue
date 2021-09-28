<template>
<HomePage />
</template>

<script>
import HomePage from "./pages/HomePage.vue"

export default {
  name: 'App',
  components: {
    HomePage
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Spartan:wght@200;400&display=swap');

:root {
  --color-background:  rgb(34, 7, 19);
  --color-gradient-start: rgb(230, 62, 44);
  --color-gradient-end: rgb(209, 6, 141);
  --color-primary: rgb(235, 77, 132);
  --color-primary-light: rgb(238, 142, 164);
}

html {
  /* background-color: rgb(21, 1, 24); */
  background-color: var(--color-background);
  transition: background-color 0.3s linear;
}

#app {
  font-family: Spartan,Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 100%;
  height: 100%;
  touch-action: none;
}

.noselect {
  -webkit-touch-callout: none; /* iOS Safari */
    -webkit-user-select: none; /* Safari */
     -khtml-user-select: none; /* Konqueror HTML */
       -moz-user-select: none; /* Old versions of Firefox */
        -ms-user-select: none; /* Internet Explorer/Edge */
            user-select: none; /* Non-prefixed version, currently
                                  supported by Chrome, Edge, Opera and Firefox */
}
</style>
