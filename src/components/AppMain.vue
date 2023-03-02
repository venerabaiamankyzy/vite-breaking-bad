<script>
import CharacterList from "./CharacterList.vue";
export default {
  props: {
    characters: Array,
  },
  components: {
    CharacterList,
  },
};
</script>

<template>
  <main>
    <CharacterList :characters="characters" />
  </main>
</template>

<style lang="scss" scoped></style>
