<template>
  <div id="app">
    <div class="background"></div>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <TypingTest />


  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import TypingTest from './components/TypingTest';

export default {
  name: 'App',
  components: {
    HelloWorld,
    TypingTest,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

*{
  padding: 0px;
  margin:0px
}

  .background{
     background-color: #008080;
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: -1;
    }
</style>
