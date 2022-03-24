<template>
  <div id="app">
    <h1>Text Scrambler</h1>
    <TextScrambler/>
  </div>
</template>

<script>
import TextScrambler from './components/TextScrambler.vue'

export default {
  name: 'App',
  components: {
    TextScrambler
  }
}
</script>

<style>
#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  background-color: darkolivegreen;
}

h1 {
  color: darkseagreen;
  margin-bottom: 20px;
}
</style>
