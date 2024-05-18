<template>
  <h1>How fast u can catch me?</h1>
  <button @click="play" class="btn" :disabled="isplay">Play</button>
  <div v-if="isplay">
    <br />
    <Block :delay="delay" @endGame="EndGame"></Block>
  </div>
  <div v-if="isdone">
    <Result :result="score"></Result>
  </div>
</template>

<script>
import Block from ".././src/components/Block.vue";
import Result from ".././src/components/Results.vue";
export default {
  data() {
    return {
      isplay: false,
      isdone:false,
      delay: null,
      score: 0,
    };
  },
  components: {
    Block: Block,
    Result: Result,
  },
  methods: {
    // is start to playing
    play() {
      this.isplay = true;
      this.isdone=false;
      this.delay = 2000 + Math.random() * 5000;
    },
    // game end to show result
    EndGame(score) {
      this.score = score;
      this.isplay = false;
      this.isdone=true;
    },
  },
};
</script>

<style>
.btn {
  width: 100px;
  height: 50px;
  background-color: green;
  border-radius: 10px;
  /* color: white; */
  font-size: medium;
}
</style>
