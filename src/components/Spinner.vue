<template>
  <div class="spinner"></div>
</template>

<script>
export default {
  name: 'Spinner',
  props: {
    show_spinner: {
      type: Boolean,
      required: true
    }
  }
}
</script>

<style lang="scss">
    .spinner {
        width: 64px;
        height: 64px;
        border-radius: 64px;
        box-sizing: border-box;
        border: 8px dotted black;
        margin: 20vh auto;
        border-top-color: rgba(0,0,0,1);
        border-left-color: rgba(0,0,0,0.9);
        border-bottom-color: rgba(0,0,0,0.8);
        border-right-color: rgba(0,0,0,0.7);
        animation: rotate 1000ms infinite steps(12,end), linear;
        transform: translateZ(0px);
    }

    @keyframes rotate {  
        0% {
            transform:rotate(0deg);
        }
        100% {
            transform:rotate(360deg);
        } 
    }
</style>