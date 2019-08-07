<template>
  <div id="app">
    
    <Countdown date="Feburary 22, 2020"/>
     
  </div>
</template>

<script>
import Countdown from './components/Countdown.vue'

export default {
  
  components: {
    
    Countdown
  }
}
</script>

<style>
#app {
   align-items: center;
  bottom: 0;
  background-color: #000000;
  display: flex;
  justify-content: center;
  left: 0;
  position: absolute;
  right: 0;
  top:0;
}
</style>
