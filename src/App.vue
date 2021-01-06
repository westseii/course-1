<template>
  <h2>{{ bookNum }} {{ bookTitles.title }}</h2>
</template>

<script>
import { ref, reactive } from "vue";

export default {
  setup() {
    const bookNum = ref("Scooter");
    const bookTitles = reactive({
      title: "bob's bobs",
      title2: "bob's bobs 2: the bobbening",
    });
    return {
      bookNum,
      bookTitles,
    };
  },
};
</script>

<style scoped>
</style>
