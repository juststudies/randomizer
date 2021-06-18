<template>
  <div id="app">
    <h1>Randomizer</h1>
    <Main />
  </div>
</template>

<script>
import Main from './components/Main.vue';

export default {
  name: 'App',
  components:{
    Main
  }
  
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto&family=Shadows+Into+Light&display=swap');   
  
  body{
    font-family: 'Shadows Into Light', cursive;
    background-color: #010a01;
  }

  #app{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  #app h1{
    font-size: 5em;
    color: #fff;
    text-shadow:
      0 0 7px #fff,
      0 0 10px #fff,
      0 0 21px #fff,
      0 0 42px #f09,
      0 0 82px #f09,
      0 0 92px #f09,
      0 0 102px #f09,
      0 0 151px #f09;
    animation: pulsate 0.11s ease-in-out infinite alternate; 
  }

  @keyframes pulsate {
    100% {

      text-shadow:
      0 0 4px #fff,
      0 0 11px #fff,
      0 0 19px #fff,
      0 0 40px #f09,
      0 0 80px #f09,
      0 0 90px #f09,
      0 0 100px #f09,
      0 0 150px #f09;
  
    }
  
    0% {

      text-shadow:
      0 0 4px #fff,
      0 0 10px #fff,
      0 0 18px #fff,
      0 0 38px #f09,
      0 0 73px #f09,
      0 0 80px #f09,
      0 0 94px #f09,
      0 0 140px #f09;

    }
  }

  @media screen and (max-width: 800px){
    #app h1{
      font-size: 4.5em;
    }
  }

  @media screen and (max-width: 600px){
    #app h1{
      font-size: 2.5em;
    }
  }

</style>
