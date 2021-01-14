<template>
  <div class="wrapper">
    <div class="label">
      <label :for="name">{{ name }}</label>
      <div class="error">
        <small>{{ isError }}</small>
      </div>
    </div>
    <input v-model="textValue" :id="name" type="text" />
  </div>
</template>

<script>
  export default {
    props: {
      name: {
        type: String,
        required: true,
      },
      rules: {
        type: Object, // ? min, required
      },
    },

    data() {
      return {
        textValue: "",
      };
    },

    computed: {
      isError() {
        if (this.rules.required && this.textValue.length === 0) {
          return "Required";
        } else if (this.textValue.length < this.rules.min) {
          return "Too short";
        }
      },
    },
  };
</script>

<style scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    padding: 0px 8px;
  }
  .label {
    align-items: center;
    display: flex;
    justify-content: space-between;
  }
  .error {
    color: red;
    user-select: none;
  }
  input {
    background: none;
    border-radius: 4px;
    border: 1px solid silver;
    color: black;
    display: block;
    font-size: 1.6rem;
    margin: 4px 0px;
    padding: 8px;
  }
</style>
