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
  <section class="main position-relative">
    <div class="dropdown position-absolute">
      <button
        class="btn btn-secondary dropdown-toggle"
        type="button"
        data-bs-toggle="dropdown"
        aria-expanded="false"
      >
        Alien
      </button>
      <ul class="dropdown-menu">
        <li><a class="dropdown-item" href="#">Action</a></li>
        <li><a class="dropdown-item" href="#">Another action</a></li>
        <li><a class="dropdown-item" href="#">Something else here</a></li>
      </ul>
    </div>
    <div class="container">
      <div class="center-content">
        <div class="banner">
          <p>Founded {{ characters.length }} cards</p>
        </div>
        <div
          class="row row-cols-2 row-cols-md-6 gap-5 justify-content-center align-items-center"
        >
          <div v-for="character in characters" class="col">
            <div class="image" v-for="characterimage in character.card_images">
              <img
                class="img-fluid"
                :src="characterimage.image_url"
                alt="cards"
              />
            </div>

            <div
              class="desc d-flex flex-column gap-3 align-items-center justify-content-between"
            >
              <h3 class="text-center">{{ character.name }}</h3>
              <p>{{ character.archetype }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style lang="scss" scope>
@use "../assets/scss/partials/_variables.scss" as *;
.main {
  min-height: 100vh;
  border: 80px solid $bg-main-color;

  .img {
    max-width: 100%;
    max-height: 100%;
  }
}
.center-content {
  padding: 20px;
}

.banner {
  background-color: $bg-black;
  color: white;
  padding: 20px;
  margin-top: 30px;
}
.row {
  padding: 0 6px;

  .col {
    background-color: $bg-main-color;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 20px;
    margin-bottom: 10px;
    min-height: 400px;

    h3 {
      font-size: 1rem;
      color: aliceblue;
    }
  }
}

.dropdown {
  left: 9px;
  top: -6%;
}

.btn {
  background-color: aliceblue;
  border: 1px solid aliceblue;
  color: $bg-black;
  padding: 6px 50px;
  text-align: left;
}
</style>
