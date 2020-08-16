<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <button @click="addcount">Re-render App {{ count }} times</button>
    </div>
    <HelloWorld :msg="`Welcome to Your Vue.js App ${count}`"/>
  </div>
</template>

<script>
import { ref, onMounted, onRenderTracked, onRenderTriggered } from 'vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  setup() {
    const count = ref(0);
    let addcount = () => {
      console.log('---------------------------------');
      console.log(`Click button ${count.value +1} times`);
      console.log('---------------------------------');
      count.value++;
    };

    console.log('---------------------------------');
    console.log(`Setup function start`);
    console.log('---------------------------------');

    onMounted(() => {
      console.log('App.vue mounted!')
    });
    onRenderTracked((e) => {
      console.log('App.vue onRenderTracked!', e)
    });
    onRenderTriggered((e) => {
      console.log('App.vue onRenderTriggered!', e)
    });

    return { count, addcount };
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
  margin-top: 60px;
}
</style>
