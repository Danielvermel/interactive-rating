<template>
  <div class="container">

    <div class="content">
      <img class="thank-you" src="../../images/illustration-thank-you.svg" alt="Star">

      <div class="rating-selection">
        You selected {{Rating}} out of 5
      </div>

       <h1>Thank you!</h1>

      <p>
        We appreciate you taking your time to give a rating.
        If you ever need more support, don't hesitate to
        get in touch!
      </p>
    </div>

  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({
  name: 'confirmation',
})
export default class Confirmation extends Vue {
  // Props
  @Prop() private rating!: number;

  // State Variables
  private savedOption = 100;

  // Getters and Setters
  get SavedOption(): number {
    return this.savedOption;
  }

  set SavedOption(value: number) {
    this.savedOption = value;
  }

  get Rating(): number {
    return this.rating;
  }

  // Methods
  private HandleClick(option: number): void {
    this.SavedOption = option;
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  max-width: 425px;
  max-height: 425px;
  width: 95%;
  height: 95%;
  background-color: #202630;
  border-radius: 3rem;
  display: flex;
  left: 50%;
  top: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  position: absolute;
  .content {
    display: flex;
    flex-direction: column;
    position: relative;
    padding: 2rem;
    width: 100%;
    .thank-you {
      transform: scale(1);
      transform-origin: 0 0;
      -webkit-transform-origin: 0 0;
      -ms-transform-origin: 0 0;
      -moz-transform-origin: 0 0;
      display: flex;
      justify-content: center;
      margin: 0 auto;
      padding: 1rem;
      border-radius: 2rem;
    }
    h1 {
      display: flex;
      color: $white;
      text-align: center;
      margin: 0 auto;
      font-weight: 400;
      font-family: 'Overpass', sans-serif;
    }
    p {
      margin-top: 1.25rem;
      color: $grey;
      font-weight: 400;
      line-height: 1.5;
      text-align: center;
      font-family: 'Overpass', sans-serif;
    }
    .rating-selection {
      display: flex;
      flex-direction: row;
      justify-content: center;
      margin-top: 2rem;
      background-color: $darkBlue;
      border-radius: 2rem;
      margin: auto;
      padding: 0.75rem;
      color: $primary;
      font-family: 'Overpass', sans-serif;
    }
  }
}
</style>
