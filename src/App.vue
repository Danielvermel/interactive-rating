<template>
  <div id="app">
    <InteractiveRating v-if="!ConfirmationState" @ratingValue="handleConfirmationState"/>
    <Confirmation v-if="ConfirmationState" :rating="RatingValue"/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import InteractiveRating from './components/InteractiveRating.vue';
import Confirmation from './components/Confirmation.vue';

@Component({
  components: {
    InteractiveRating,
    Confirmation,
  },
})
export default class App extends Vue {
  private confirmationState = false;

  private ratingValue!: number;

  get ConfirmationState(): boolean {
    return this.confirmationState;
  }

  set ConfirmationState(value: boolean) {
    this.confirmationState = value;
  }

  get RatingValue(): number {
    return this.ratingValue;
  }

  set RatingValue(value: number) {
    this.ratingValue = value;
  }

  private handleConfirmationState(value: number): void {
    this.ConfirmationState = true;
    this.RatingValue = value;
  }
}

</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  height: 100%;
}
</style>
