<template>
  <h1 class="block" @click="hitBlock" v-if="showBlock">{{ msg }}</h1>
</template>

<script>
export default {
  name: 'Block',
  props: {
    msg: String,
    delay: Number
  },
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
      }, this.delay)
  },
  methods: {
    hitBlock: function(){
      this.showBlock = false;
      this.stopTimer();
      this.$emit("hitblock", this.reactionTime);
    },
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 1;
      }, 1)
    },
    stopTimer(){
      clearInterval(this.timer);
    }
  }
}
</script>

<style>
.block{
  border-radius: 20px;
  padding: 100px 0;
  width: 400px;
  text-align: center;
  background:  rgb(17, 155, 63);
  color: white;
  margin-top: 50px;
  margin-left: auto;
  margin-right: auto;
  cursor: pointer;
}
</style>