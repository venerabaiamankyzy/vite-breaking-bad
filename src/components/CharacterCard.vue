<script>
export default {
  props: {
    pic: String,
    name: String,
    type: String,
  },
};
</script>

<template>
  <div class="col">
    <div class="image">
      <img class="img-fluid" :src="pic" alt="cards" />
    </div>

    <div
      class="desc d-flex flex-column gap-3 align-items-center justify-content-between"
    >
      <h3 class="text-center">{{ name }}</h3>
      <p>{{ type }}</p>
    </div>
  </div>
</template>

<style lang="scss" scope></style>
