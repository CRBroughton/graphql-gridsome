<template>
  <div>
    <div v-if="launch.links.article_link" class="flex flex-col">
      <a class="mx-auto" :href="launch.links.article_link">Article Link</a>
    </div>
    <p class="mx-auto">{{ launch.mission_name }}</p>
    <p class="mx-auto">{{ launch.launch_year }}</p>
  </div>
</template>

<script>
export default {
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
</style>