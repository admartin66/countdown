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
  props: ['date'],
 

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
    /*display: inline-block;*/
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
    position: absolute;
    /*width: 180dppx;*/
    left: 1em;
    text-align: right;
}

.digit {
    color: #f70707;
  
    /*font-size: 180px;*/
    font-weight: 100;
    font-family: 'Orbitron', sans-serif;
    
   
   
}
@media screen and (min-width: 320px){
  .digit{
    font-size: calc(14px + (180 - 14) * ((100vw - 300px) / (1600 - 300)));
  }
}
@media screen and (min-width: 1000px){
  .digit{
    font-size:180px;
  }
}

</style>
