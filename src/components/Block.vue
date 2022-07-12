<template>
  <div class="block" v-if="showBlock" @click="stopTimer">CLICK ME!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer(); // We start the timer as soon as the Reaction Button appears (which is when showBlock becomes true)
    }, this.delay); // Delay has been passed as a prop from the parent component
  },

  updated() {
    // This will fire when data inside the component is updated, in this case when the timer changes showBlock to true.
    console.log("Component has been updated!");
  },

  methods: {
    startTimer() {
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10); // the setInterval function is store in a variable (this.timer) so we can stop the timer later using clearInterval + the name of the timer variable
    },
    stopTimer() {
      clearInterval(this.timer);
      this.$emit("end", this.reactionTime);
    },
  },
};
</script>

<style>
.block {
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0;
  margin: 40px auto;
}
</style>
