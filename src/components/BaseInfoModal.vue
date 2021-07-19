<template>
  <div
    v-if="showModal"
    class="w-full bg-gray-700 flex flex-col bottom-2 p-4 text-sm rounded m-auto"
  >
    <div v-if="launch.links.article_link" class="flex flex-col">
      <a class="mx-auto" :href="launch.links.article_link">Article Link</a>
    </div>
    <p class="mx-auto">{{ launch.mission_name }}</p>
    <p class="mx-auto">{{ launch.launch_year }}</p>
  </div>
</template>

<script>
export default {
  props: {
    launch: {
      type: Object,
      required: true,
    },
    showModal: {
      type: Boolean,
      required: true,
    },
  },
};
</script>

<style lang="scss" scoped>
</style>