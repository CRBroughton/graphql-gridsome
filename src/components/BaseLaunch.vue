
<template>
  <div class="grid grid-cols-1 max-w-screen-sm">
    <div
      v-for="launch in launches[0]"
      :key="launch.id"
      class="text-white flex flex-col border-4 border-gray-200"
    >
        <img v-lazy="launch.links.flickr_images[0]" />
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
      " { launchesPast { launch_success launch_year links { article_link flickr_images } mission_name rocket { rocket_name } } } "
    );

    const filteredLaunches = launches.launchesPast.filter(
      (iterator) => iterator.links.flickr_images.length > 0
    );
    this.launches.push(filteredLaunches);
  },
};
</script>

<style scoped>
</style>