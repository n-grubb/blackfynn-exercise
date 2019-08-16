<template>
  <div v-if="display" class="error-message">
      <slot></slot>
  </div>
</template>

<script>
export default {
  name: 'ErrorMessage',
  props: {
    display: {
      type: Boolean,
      required: true
    }
  }
}
</script>

<style lang="scss">
    .error-message {
        width: 100%;
        padding: 1em;
        background-color: rgb(255, 0, 0, .25);
        border-radius: 4px;
        p {
            margin: 0;
        }
    }
</style>