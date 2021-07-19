<template>
  <div>
    <base-launch />
  </div>
</template>

<script lang="ts">
import BaseLaunch from "../components/BaseLaunch.vue";

export default {
  components: {
    BaseLaunch,
  },
};
</script>

<style>
/* ---------------------------------- */
/* BASIC SETUP */
/* ---------------------------------- */

/*Include padding and border in the element's total width and height*/
*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  margin: 0; /*remove all margin and padding
                from elements at the start*/
  padding: 0;
  list-style: none;
  text-decoration: none;
}

html {
  scroll-behavior: smooth;
}

html,
body {
  background-color: #fff;
  color: #555;
  font-family: "Open-Sans", "Arial", sans-serif;
  font-weight: 300;
  font-size: 20px;
  text-rendering: optimizeLegibility;
  overflow-x: hidden; /*stops overflow on the x axis, 
                        usually shows as a white strip
                        from top to bottom of page*/
}
</style>
