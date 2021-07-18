
<template>
  <div class="">
    <div v-for="launch in launches[0]" :key="launch.id" class="w-96">
      <img :src="launch.links.flickr_images" alt="" />
      <a :href="launch.links.article_link">{{launch.links.article_link}}</a>
      <p>{{ launch.mission_name }}</p>
      <p>{{ launch.launch_year }}</p>
      <!-- <a :href="launch.links.article_link">{{ launch.links.article_link }}</a> -->
    </div>
  </div>
</template>

<script>
import { GraphQLClient } from "graphql-request";

export default {
  data() {
    return {
      launches: [],
    };
  },
  async mounted() {
    const client = new GraphQLClient("http://api.spacex.land/graphql/");
    const launches = await client.request(
      " { launchesPast(limit: 10) { launch_success launch_year links { article_link flickr_images } mission_name rocket { rocket_name } } } "
    );

      const filteredLaunches = launches.launchesPast.filter(iterator => iterator.links.flickr_images.length > 0)
      this.launches.push(filteredLaunches)
      console.log("test", this.launches)

  },
};
</script>

<style scoped>
</style>