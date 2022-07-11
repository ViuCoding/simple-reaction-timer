<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>

  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <p v-if="showResults">Reaction time is: {{ score }}ms</p>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000; // This will generate a number between 2000ms and 7000ms
      this.isPlaying = true;
      this.showResults = false;
      console.log(this.delay);
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.showResults = true;
      this.isPlaying = false;
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
  color: #444;
  margin-top: 60px;
}
</style>
