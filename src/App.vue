<template>
  <div id="app">
    <h1>Joke Api</h1>
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld :getJoke="getJoke" :joke="joke" />
    <button @click="getJoke">Get Joke</button>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  data() {
    return {
      joke: "",
    };
  },
  beforeMount() {
    this.getJoke();
  },
  methods: {
    async getJoke() {
      const res = await fetch("https://v2.jokeapi.dev/joke/Any?type=single");
      const data = await res.json();
      this.joke = data.joke;
    },
  },
  components: {
    HelloWorld,
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
