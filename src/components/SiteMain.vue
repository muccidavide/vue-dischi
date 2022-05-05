<template>
  <main>
    <div class="container pt-3">
      <div class="row row-cols-1 row-cols-sm-2 row-cols-md-3 row-cols-lg-4 row-cols-xl-5  align-items-center" v-if="!loading">
        <CardComponent
          :album="album"
          v-for="(album, index) in albums"
          :key="index"
        />
      </div>
      <div
        v-else class="d-flex min-vh-100 align-items-center justify-content-center">
        <div class="div">
          <h2>Loading....</h2>
          <h3 v-if="error !== null">{{ error }}</h3>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import CardComponent from "@/components/CardComponent.vue";
export default {
  name: "SiteMain",
  components: {
    CardComponent,
  },
  data() {
    return {
      API_URL: "https://flynn.boolean.careers/exercises/api/array/music",
      albums: null,
      error: null,
      loading: true,
    };
  },
  methods: {
    callApi() {
      axios
        .get(this.API_URL)
        .then((response) => {
          this.albums = response.data.response;
          this.loading = false;
        })
        .catch((error) => {
          console.error();
          error;
          this.error = `Sorry There is a problem! ${error}`;
        });
    },
  },
  mounted() {
    this.callApi();
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: $ds-dark;
  padding-top: 2rem;

  h2,h3 {
    color: $ds-white;
  }
}
</style>