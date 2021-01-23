<template>
  <h1 class="result" v-if="showResult">{{ msg }}</h1>
  <h3 class="result" :class="{ green: green, yellow: yellow, red: red }" v-if="showResult">{{ rank }}</h3>
  <h3 class="result" v-if="showResult">Your Response Time: {{ resultScore }} ms</h3>
</template>

<script>
export default {
  name: 'Result',
  props: {
    msg: String,
    resultScore: Number,
    showResult: Boolean
  },
  data() {
    return{
      rank: null,
      green: false,
      yellow: false,
      red: false
    }
  },
  updated(){
    if(this.resultScore < 100){
      this.rank = "SPEEEED AND POWEEEEER!!!";
      this.green = true;
      this.yellow = this.red = false;
    } else if (this.resultScore < 300){
      this.rank = "Go Fasteeer!";
      this.yellow = true;
      this.green = this.red = false;
    } else {
      this.rank = "Are you sleeping? WAKE UP!!!";
      this.red = true;
      this.green = this.yellow = false;
    }
  }
}
</script>

<style>
.result{
  padding: 15px 0;
  width: 500px;
  text-align: center;
  color: rgb(17, 155, 63);
  margin: 10px auto;
}

.green{
  border: 2px solid  rgb(17, 155, 63);
  border-radius: 20px;
  padding: 15px 0;
  width: 400px;
  text-align: center;
  color: white;
  background: rgb(17, 155, 63);
  margin: auto;
}

.yellow{
  border: 2px solid  yellow;
  border-radius: 20px;
  padding: 15px 0;
  width: 400px;
  text-align: center;
  color: black;
  background: yellow;
  margin: auto;
}

.red{
  border: 2px solid  red;
  border-radius: 20px;
  padding: 15px 0;
  width: 400px;
  text-align: center;
  color: white;
  background: red;
  margin: auto;
}
</style>