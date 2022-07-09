<template>
  <div class="container">

    <div class="content">
      <img class="thank-you" src="../../images/illustration-thank-you.svg" alt="Star">

      <div class="rating-selection">
        You selected {{Rating}} out of 5
      </div>

       <h1>Thank you</h1>

      <h3>
        We appreciate you taking your time to give a rating.
        If you ever need more support, don't hesitate to
        get in touch!
      </h3>
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
  width: 450px;
  height: 450px;
  background-color: #202630;
  border-radius: 3rem;
  display: flex;
  margin: auto;
  left: 50%;
  top: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  position: absolute;
  .content {
    display: flex;
    flex-direction: column;
    position: relative;
    width: 100%;
    padding: 2.5rem;
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
      color: white;
      text-align: center;
      margin: 0 auto;
    }
    h3 {
      margin-top: 1.25rem;
      color: #6f757f;
      font-weight: 400;
      line-height: 1.5;
      text-align: center;
    }
    .rating-selection {
      display: flex;
      flex-direction: row;
      justify-content: center;
      margin-top: 2rem;
      background-color: #262e38;
      border-radius: 2rem;
      margin: auto;
      padding: 0.75rem;
      color: #FC7614;
    }
  }

}
</style>
