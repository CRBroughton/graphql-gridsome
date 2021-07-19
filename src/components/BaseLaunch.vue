
<template>
  <div class="grid grid-cols-1 max-w-screen-sm min-w-min">
    <div
      v-for="launch in launches[0]"
      :key="launch.id"
      class="text-white border-4 border-gray-200 transition duration-500 ease-in-out transform hover:scale-105 hover:border-gray-400 cursor-pointer max-h-screen m-4"
      @click="toggleModal"
    >
        <base-info-modal :launch="launch" :showModal="showModal" class="absolute"/>
        <img v-lazy="launch.links.flickr_images[0]" />
      </div>
    </div>
</template>

<script>
import { GraphQLClient } from "graphql-request";
import BaseInfoModal from "./BaseInfoModal.vue";

export default {
  components: {
    BaseInfoModal,
  },
  data() {
    return {
      launches: [],
      showModal: false,
    };
  },
  async mounted() {
    const client = new GraphQLClient("http://api.spacex.land/graphql/");
    const launches = await client.request(
      " { launchesPast { launch_year links { article_link flickr_images } mission_name } } "
    );

    const filteredLaunches = launches.launchesPast.filter(
      (iterator) => iterator.links.flickr_images.length > 0
    );
    this.launches.push(filteredLaunches);
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    }
  }
};
</script>

<style scoped>
</style>