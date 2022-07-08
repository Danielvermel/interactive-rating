<template>
  <div class="container">

    <div class="content">
      <img class="star" src="../../images/icon-star.svg" alt="Star">

      <h1>How did we do?</h1>

      <h3>
          Please let us know how we did with your support request.
          All feedback is appreciated to help us improve our offering!
      </h3>

      <div class="rating-container">
        <button v-for="i, index in 5" :key="index" class="rating-content"
                :class="{'selected': index === SavedOption}" @click="HandleClick(index)">
          {{i}}
        </button>
      </div>

      <button class="submit">Submit</button>
    </div>

  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator';

@Component({
  name: 'interactive-rating',
})
export default class InteractiveRating extends Vue {
  // Props
  @Prop() private msg!: string;

  // State Variables
  private savedOption = 100;

  // Getters and Setters
  get SavedOption(): number {
    console.warn(this.savedOption);
    return this.savedOption;
  }

  set SavedOption(value: number) {
    this.savedOption = value;
  }

  // Methods
  private HandleClick(option: number): void {
    this.SavedOption = option;
    // console.warn(this.savedOption);
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
    .star {
      transform: scale(1);
      transform-origin: 0 0;
      -webkit-transform-origin: 0 0;
      -ms-transform-origin: 0 0;
      -moz-transform-origin: 0 0;
      display: flex;
      justify-content: left;
      margin-right: auto;
      background-color: #262e38;
      padding: 1rem;
      border-radius: 2rem;
    }
    h1 {
      display: flex;
      color: white;
      margin-top: 2rem;
    }
    h3 {
      margin-top: 1rem;
      color: #6f757f;
      font-weight: 400;
      line-height: 1.5
    }
    .rating-container {
      display: flex;
      flex-direction: row;
      justify-content: space-between;
      margin-top: 2rem;
      .rating-content {
        padding: 1.3rem;
        display: flex;
        justify-content: center;
        font-size: 1.25rem;
        border-radius: 2rem;
        width: 4rem;
        height: 4rem;
        background-color: #262e38;
        color: #6F7880;
        cursor: pointer;
        border: none;
        &:hover {
          background-color: #FC7614;
          color: white;
        }
        &.selected{
          background-color: #7D8899;
          color: white;
        }
      }
    }
    button.submit {
      width: 100%;
      color: white;
      background-color: #FC7614;
      margin-top: 2rem;
      border-radius: 2rem;
      border: none;
      padding: 1rem 0;
      text-transform: uppercase;
      letter-spacing: 3px;
      font-weight: 600;
      cursor: pointer;
      &:hover {
         color: #FC7614;
        background-color: white;
      }
    }
  }

}
</style>
