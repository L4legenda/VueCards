<template>
  <div id="app">
	<Card/>
  </div>
</template>

<script>
import Card from './components/card.vue'

export default {
  name: 'app',
  components: {
    Card
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
