<script>
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";
import axios from "axios";
import { store } from "./data/store";

export default {
  data() {
    return {
      store, //o store: store
    };
  },

  components: {
    AppMain,
    AppHeader,
  },
  created() {
    axios.get(store.endpoint).then((response) => {
      console.log(response);
      store.characters = response.data.data;
    });
  },
};
</script>

<template>
  <AppHeader />
  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/style.scss";
</style>
