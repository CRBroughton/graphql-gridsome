
<template>
  <div class="grid grid-cols-1 max-w-screen-sm min-w-min">
    <div
      v-for="(launch, index) in paginatedOrders"
      :key="index"
      class="text-white border-4 border-gray-200 transition duration-500 ease-in-out transform hover:scale-105 hover:border-gray-400 cursor-pointer max-h-screen m-4"
      @click="toggleModal"
    >
        <base-info-modal :launch="launch" :showModal="showModal" class="absolute"/>
        <img v-lazy="launch.links.flickr_images[0]" />
      </div>
      <button @click="loadMore" v-if="page * maxLaunchesPerPage" >Load More</button>
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
      page: 1,
      maxLaunchesPerPage: 4,
      showModal: false,
      componentsLoaded: false
    };
  },
  async mounted() {
    const client = new GraphQLClient("https://api.spacex.land/graphql/");
    const launches = await client.request(
      " { launchesPast { launch_year links { article_link flickr_images } mission_name } } "
    );

    const filteredLaunches = launches.launchesPast.filter(
      (iterator) => iterator.links.flickr_images.length > 0
    );
    this.launches.push(filteredLaunches);
    this.componentsLoaded = true;
  },
  computed: {
    paginatedOrders() {
      if (!this.componentsLoaded) {
        return null;
      }
      return this.launches[0].slice(0, this.page * this.maxLaunchesPerPage);
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal;
    },
    loadMore() {
      this.page += 1;
    }
  }
};
</script>

<style scoped>
</style>