<template>
  <button @click="incrementNum">num++</button>
  <p>"{{ userInput }}"</p>
  <br />
  <input v-model="userInput" type="text" />
  <p class="card" v-for="num in thirdNums" :key="num">{{ num }}</p>
  <p :class="getClass(num)">{{ num }}</p>
  <p>Total: {{ allThirdNums }}</p>
</template>

<script>
  export default {
    data() {
      return {
        userInput: "",
        num: 0,
        nums: [],
      };
    },
    methods: {
      getClass(num) {
        return this.isThird(num) ? "red" : "blue";
      },
      incrementNum() {
        this.num++;
        this.nums.push(this.num);
      },
      isThird(num) {
        return num % 3 === 0;
      },
    },
    computed: {
      thirdNums() {
        return this.nums.filter((n) => this.isThird(n));
      },
      allThirdNums() {
        return this.thirdNums.reduce((acc, n) => acc + n, 0);
      },
    },
  };
</script>

<style scoped>
  .card {
    border-radius: 4px;
    box-shadow: 0 0 4px 0 rgba(16, 16, 16, 0.1);
    margin: 12px;
    padding: 12px;
    user-select: none;
    width: 200px;
  }
  .card:hover {
    box-shadow: 0 0 8px 0 rgba(16, 16, 16, 0.15);
  }
  .red {
    color: red;
  }
  .blue {
    color: blue;
  }
</style>
