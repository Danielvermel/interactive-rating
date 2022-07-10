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
                :class="{'selected': index === SavedOption}" @click="handleClick(index)">
          {{i}}
        </button>
      </div>

      <button class="submit" @click="handleSubmit">Submit</button>
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
    return this.savedOption;
  }

  set SavedOption(value: number) {
    this.savedOption = value;
  }

  // Methods
  private handleClick(option: number): void {
    this.SavedOption = option;
  }

  private handleSubmit(): void {
    if (this.SavedOption !== 100) {
      this.$emit('ratingValue', this.SavedOption);
    } else {
      alert("You didn't select any rating!");
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container {
  max-width: 450px;
  max-height: 450px;
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
    padding: 2.5rem;
    width: 100%;
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
      color: $white;
      margin-top: 2rem;
      font-weight: 700
    }
    h3 {
      margin-top: 1rem;
      color: $grey;
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
@media (max-width: 465px) {
  .container {
    // max-height: 485px;
    h1 {
      font-size: 1.5rem;
    }
    h3 {
      font-size: 1rem;
    }
    .rating-content  {
      transform: scale(0.8)
    }
  }
}
</style>
