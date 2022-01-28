<template>
  <div class="app-container">
    <h2>Task One</h2>
    <HelloWorld msg="Hello World!" />
    <!-- Your solution to task one -->

    <MyMessageList/>

    <hr>

    <h2>Task Two</h2>
    <HelloWorld msg="Hello World Two!" />
    <!-- Your solution to task two -->

    <TrimMessage />
    
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import MyMessageList from './components/MyMessageList.vue'
import TrimMessage from './components/TrimMessage.vue'

export default {
  name: 'App',
  components: {
    HelloWorld,
    MyMessageList,
    TrimMessage
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
.app-container {
  max-width: min(100vw, 1200px);
  margin: 0 auto;
}
</style>
