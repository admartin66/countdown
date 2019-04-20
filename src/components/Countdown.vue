<template>
<div class="block">
  <pre class="digit"> {{days | two_digits}}   {{hours | two_digits }} : {{minutes | two_digits}} : {{seconds | two_digits}}</pre>

</div>
</template>

<script>
export default {
  
  mounted() {
    window.setInterval(() => {
      this.now = Math.trunc((new Date()).getTime() / 1000);
    },1000);
    }

  ,
  props: {
    
    date : String
  },
 

  data() {
    return {
      now: Math.trunc((new Date()).getTime()/ 1000)
    }
  },
  computed:{

    normalizedDate: function () {
      return Math.trunc(Date.parse(this.date) / 1000)
    },
    seconds() {
      return (this.normalizedDate - this.now) % 60;
    },

    minutes() {
      return Math.trunc((this.normalizedDate - this.now) / 60) % 60;
    },

    hours() {
      return Math.trunc((this.normalizedDate - this.now) / 60 / 60) % 24;
    },
    days(){
      return Math.trunc(( this.normalizedDate - this.now ) /60 /60 / 24);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
@import url(https://fonts.googleapis.com/css?family=Orbitron);

.block {
    display: inline-block;
    /*flex-direction: row;*/
    /*margin: 20px;*/
    position: absolute;
    width: 180dppx;
    left: 1em;
    text-align: right;
}

.text {
    color: #1abc9c;
    font-size: 40px;
    font-family: 'Roboto Condensed', serif;
    font-weight: 400;
    margin-top:10px;
    margin-bottom: 10px;
    text-align: center;
}

.digit {
    color: #f70707;
    font-size: 180px;
    font-weight: 100;
    font-family: 'Orbitron', sans-serif;
    
   
    /*text-align: center;*/
}
</style>
