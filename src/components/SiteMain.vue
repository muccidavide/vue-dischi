<template>
<main>


  <div class="container pt-3">
    <div class="row row-cols-5 align-items-center">
      <CardComponent :album="album"
        v-for="(album, index) in discs"
        :key="index"
      />
    </div>
  </div>
</main>
</template>

<script>
import axios from "axios";
import CardComponent from "@/components/CardComponent.vue"
export default {
  name: "SiteMain",
  components: {
      CardComponent,
  },
  data() {
    return {
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
      discs: null,
      error: null,
    };
  },
  methods: {
    callApi() {
      axios
        .get(this.API_URL)
        .then((response) => {
          this.discs = response.data.response;
          this.loading = false;
        })
    },
  },
  mounted() {
    this.callApi();
  },
};
</script>

<style lang="scss" scoped>

main{
    background-color: $ds-dark;
    padding-top: 2rem;

}




</style>