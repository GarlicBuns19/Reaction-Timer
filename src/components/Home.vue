<template>
  <h1>Reaction timer</h1>
  <button @click="startTest" class="startBtn">Start Test</button>
  <h2 v-if="score != null">Reaction time is {{ score }}ms</h2>
  <h3 v-if="rank != ''">{{ rank }}</h3>
  <Block v-if="begin" :delay="delay" @end="endGame" />
</template>

<script>
import Block from "./Block.vue";

export default {
  components: {
    Block,
  },
  data() {
    return {
      begin: false,
      delay: null,
      score: null,
      rank: "",
    };
  },
  methods: {
    startTest() {
      this.begin = true;
      this.delay = 2000 + Math.random() * 5000;
      this.score = null;
      this.rank = "";
      // console.log(this.begin)
      // console.log(this.delay)
      // console.log('Test started')
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.begin = false;
      if (this.score < 250) {
        this.rank = "Ultra spedd";
      } else if (this.score <= 500) {
        this.rank = "Normal speed";
      } else {
        this.rank = "You need to speed up";
      }
    },
  },
};
</script>

<style lang="sass">
.startBtn
    margin: 20px 0 0 0
</style>