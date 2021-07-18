
<template>
  <div>
    <div v-for="(launch, index) in launches[0]" :key="launch.id">
      <p>{{ launch }} -- {{ index }}</p>
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
      " { launchesPast(limit: 10) { mission_name }  }"
    );
    this.launches.push(launches.launchesPast);
    console.log(JSON.stringify(this.launches[0]));
  },
};
</script>

<style scoped>
</style>