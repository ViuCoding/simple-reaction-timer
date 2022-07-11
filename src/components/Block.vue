<template>
  <div class="block" v-if="showBlock">Click Me!</div>
</template>

<script>
export default {
  props: ["delay"],
  data() {
    return {
      showBlock: false,
    };
  },
  mounted() {
    console.log("Component has been mounted!");
    setTimeout(() => {
      this.showBlock = true;
    }, this.delay);
  },

  updated() {
    // This will fire when data inside the component is updated, in this case when the timer changes showBlock to true.
    console.log("Component has been updated!");
  },

  unmounted() {
    console.log("Unmounted");
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
