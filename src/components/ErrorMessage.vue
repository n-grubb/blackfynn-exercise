<template>

    <transition name="fade">
        <div v-if="display" class="error-message">
            <slot></slot>
        </div>
    </transition>

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
        margin-bottom: .5em;

        p {
            margin: 0;
            font-size: .75em;
        }
    }

    .fade-enter-active, .fade-leave-active {
        transition: opacity 0.25s ease-out;
    }

    .fade-enter, .fade-leave-to {
        opacity: 0;
    }
</style>