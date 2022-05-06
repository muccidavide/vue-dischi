<template>
  <header class="row justify-content-between align-items-center">
    <div class="logo col">
      <img
        height="40px"
        src="https://cantabrialabsdifacooper.it/wp-content/uploads/2021/03/png-clipart-spotify-logo-spotify-computer-icons-podcast-music-apps-miscellaneous-angle-1-e1614848134495.png"
        alt=""
      />
    </div>
    <div class="col-4">
      
        <div class="mb-3">
          <label for="genre" class="form-label text-white"
            >Select Music Genre:</label
          >
          <select
            class="form-control"
            name="genre"
            id="genre"
            v-model="selectedGenre"
            @click="selectGenre"
            placeholder="Select a Genre"
          >
            <option disabled>Select Genre</option>
            <option>All</option>
            <option>Pop</option>
            <option>Jazz</option>
            <option>Metal</option>
            <option>Rock</option>
          </select>
        </div>
  
    </div>
  </header>
</template>

<script>
import state from "@/state.js";

export default {
  name: "SiteHeader",
  data() {
    return {
      selectedGenre: "",
    };
  },
  methods: {
    selectGenre() {
      state.selectedGenre = this.selectedGenre;
      console.log(state.selectedGenre);
    },
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: $ds-primary;
  .logo {
    padding: 0.5rem 2rem;
  }
  .col-4 {
    background-color: $ds-primary;
    padding-right: 2rem;
    .form-control {
      background-color: $ds-white;
    }
  }
}
</style>
