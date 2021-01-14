<template>
  <div class="wrapper">
    <!-- <input v-model="userType" type="password" />
    <div class="error" v-if="isError(userType)">
      <small>*Too short</small>
    </div>
    <p>{{ userType }}</p>
    <br /><br /> -->

    <button @click="incrementNum">num++</button>
    <p
      :class="getClass(num)"
      :style="{ 'font-size': '4rem', 'margin-left': '24px' }"
    >
      {{ num }}
    </p>
    <div class="contain-thirds">
      <p class="card" v-for="num in thirdNums" :key="num">{{ num }}</p>
    </div>
    <p>Total: {{ totalThirdNums }}</p>
    <hello
      :style="{ 'line-height': '3rem' }"
      :text="`Numbers: ${nums.join(', ')}`"
      color="#0066cc"
    />
    <br /><br />

    <my-input name="Username:" :rules="{ required: true, min: 8 }" />
    <my-input name="Password:" :rules="{ required: true, min: 12 }" />
    <my-button color="white" background="darkslateblue" text="Submit" />
  </div>
</template>

<script>
  import Hello from "./components/Hello.vue";
  import MyButton from "./components/MyButton.vue";
  import MyInput from "./components/MyInput.vue";

  export default {
    components: { Hello, MyButton, MyInput },

    data() {
      return {
        num: 0,
        nums: [],
        userType: "",
        valid: false,
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
      isError(text) {
        return text.length < 8;
      },
    },

    computed: {
      thirdNums() {
        return this.nums.filter((n) => this.isThird(n));
      },
      totalThirdNums() {
        return this.thirdNums.reduce((acc, n) => acc + n, 0);
      },
    },
  };
</script>

<style scoped>
  .wrapper {
    width: 400px;
  }
  .contain-thirds {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  .card {
    border-radius: 2px;
    box-shadow: 1px 2px 4px 2px rgba(24, 24, 24, 0.1);
    margin: 16px;
    padding: 16px;
    user-select: none;
    width: 80px;
  }
  .card:hover {
    box-shadow: 1px 2px 6px 2px rgba(24, 24, 24, 0.15);
  }
  .error {
    color: #cc3399;
    user-select: none;
  }
  .blue {
    color: #0066cc;
  }
  .red {
    color: #cc3399;
  }
  button {
    background: darkslateblue;
    border-radius: 4px;
    border: none;
    color: white;
    cursor: pointer;
    margin: 8px;
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
</style>
