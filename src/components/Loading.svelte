<script type="typescript">
  import { fade } from "svelte/transition";

  export let size: number = 40; // width and height
  export let style: string = ""; // external styling
  export let speed: number = 1400; // speed in miliseconds
</script>

<div
  class="Loading"
  style="width: {size}px; height: {size}px; --speed: {speed}ms; {style}"
  in:fade={{ duration: 140 }}>
  <svg viewBox="22 22 44 44">
    <circle
      class="spinner"
      cx="44"
      cy="44"
      r="20.2"
      fill="none"
      stroke-width="3.6" />
  </svg>
</div>

<style lang="sass">

  .Loading
    display: block
    line-height: 1
    color: var(--inverted-elements-color)
    animation: spinnerParentAnimation var(--speed) linear infinite
    margin: 0 auto

    svg
      .spinner
        animation: spinnerAnimation var(--speed) ease-in-out infinite
        stroke-dasharray: 80px, 200px
        stroke-dashoffset: 0
        stroke: currentColor

  @-webkit-keyframes spinnerParentAnimation
    100%
      transform: rotate(360deg)

  @-webkit-keyframes spinnerAnimation
    0%
      stroke-dasharray: 1px, 200px
      stroke-dashoffset: 0px
    
    50%
      stroke-dasharray: 100px, 200px
      stroke-dashoffset: -15px
      
    100%
      stroke-dasharray: 100px, 200px
      stroke-dashoffset: -125px

</style>
