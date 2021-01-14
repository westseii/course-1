<template>
  <button
    :class="{ 'button-disabled': disabled }"
    :style="{ color, background }"
  >
    {{ text }}
  </button>
</template>

<script>
  export default {
    props: {
      text: {
        type: String,
        default: "Button",
      },
      color: {
        type: String,
        default: "black",
      },
      background: {
        type: String,
        default: "green",
      },
      disabled: {
        type: Boolean,
      },
    },
  };
</script>

<style scoped>
  button {
    border-radius: 4px;
    border: none;
    cursor: pointer;
    margin: 4px 8px;
    padding: 12px;
  }
  button:hover {
    filter: brightness(1.2);
    position: relative;
  }
  button:active {
    position: relative;
    top: 1px;
  }
  .button-disabled {
    cursor: not-allowed;
    filter: opacity(0.8) brightness(0.8);
  }
</style>
