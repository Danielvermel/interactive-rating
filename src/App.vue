<template>
  <div id="app">
    <InteractiveRating />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import InteractiveRating from './components/InteractiveRating.vue';

@Component({
  components: {
    InteractiveRating,
  },
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
}
</style>
