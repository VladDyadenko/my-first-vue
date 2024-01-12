<template>
  <h1>{{ title }}</h1>
  <ButtonMain btnName="increment" @click="increment" />
  <ButtonMain btnName="decrement" @click="decrement" />
  <ButtonMain btnName="reset" @click="reset" />
</template>

<script>
import ButtonMain from "./components/ButtonMain.vue";
export default {
  name: "App",
  components: {
    ButtonMain,
  },
  data() {
    return {
      emountClick: 0,
    };
  },
  computed: {
    title() {
      return `Amount of click: ${this.emountClick}`;
    },
  },
  methods: {
    increment() {
      return (this.emountClick += 1);
    },
    decrement() {
      return (this.emountClick -= 1);
    },
    reset() {
      return (this.emountClick = 0);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
