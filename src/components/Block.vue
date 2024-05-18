<template>
  <div @click="Click" class="block" v-if="showBlock">
    <h1>Click Here </h1>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showBlock: false,
      score: 0,
      timer: null,
    };
  },
  props: ["delay"],
  methods: {
    Click() {
        clearInterval(this.timer);
        this.$emit('endGame',this.score)
    },
    StartTimer() {
      this.timer = setInterval(() => {
        this.score += 50;
      }, 50);
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.StartTimer();
    }, this.delay);
  },
};
</script>

<style>
.block {
  background-color: aqua;
  width: 350px;
  height: 250px;
  margin: 0 auto;
  display: flex; /* Use Flexbox */
  justify-content: center; /* Center horizontally */
  align-items: center;
  border-radius: 10px;
}
h1 {
  text-align: center;
}
</style>
