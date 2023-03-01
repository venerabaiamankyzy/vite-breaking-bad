<script>
import axios from "axios";

export default {
  data() {
    return {
      characters: [],
    };
  },

  created() {
    axios
      .get("https://db.ygoprodeck.com/api/v7/cardinfo.php?num=10&offset=0")
      .then((response) => {
        console.log(response);
        this.characters = response.data.data;
      });
  },
};
</script>
<template>
  <div class="container">
    <section class="mt-4 px-3 pb-3">
      <div class="banner">
        <h4>Found {{ characters.length }} cards</h4>
      </div>
      <div class="row row-cols-2 row-cols-md-5 g-4 px-3">
        <div v-for="character in characters" class="col text-center bg-orange">
          <div class="bg-card">
            <div v-for="characterimage in character.card_images">
              <img
                class="img-fluid"
                :src="characterimage.image_url"
                alt="cards"
              />
            </div>
            <div class="card-info">
              <h3>{{ character.name }}</h3>
              <span>{{ character.archetype }}</span>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<style lang="scss" scope>
@use "../assets/scss/partials/_variables.scss" as *;
.banner {
  background-color: $bg-black;
  color: white;
  padding: 16px 20px;
}
.bg-card {
  background-color: $bg-main-color;
  padding: 0;
  min-height: 400px;

  img {
    width: 80%;
  }
  .card-info {
    text-align: center;

    h3 {
      font-size: 1.1rem;
      text-transform: uppercase;
      color: white;
      padding-top: 10px;
    }

    span {
      font-size: 1rem;
    }
  }
}
</style>
