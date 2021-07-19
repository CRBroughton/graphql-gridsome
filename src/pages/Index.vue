<template>
  <div class="flex flex-col bg-gray-800 text-white">
    <base-launch
      class="mx-auto"
    />
    <the-footer />
  </div>
</template>

<script lang="ts">

import BaseLaunch from "../components/BaseLaunch.vue";
import TheFooter from "../components/TheFooter.vue";

export default {
  components: {
    BaseLaunch,
    TheFooter,
  },
  metaInfo: {
    title: 'SpaceX',
    meta: [
      {
        name: 'author',
        content: 'Craig Broughton'
      }
    ],
  }
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
