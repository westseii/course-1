<template>
  <div :style="{ color }">{{ text }}</div>
</template>

<script>
  export default {
    props: {
      color: {
        type: String,
        default: "green",
      },
      text: {
        type: String,
        default: "Lorem ipsum dolor sit amet consectetur adipisicing elit.",
      },
    },
  };
</script>

<style scoped>
</style>
