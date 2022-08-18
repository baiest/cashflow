<template>
  <teleport to='body'>
    <transition name="show">
    <section class="modal" v-show="isOpen">
      <div class="modal__container">
        <h3>
          <slot name="header"></slot>
        </h3>
        <section>
          <slot name="content"></slot>
        </section>
        <button><img src="@/assets/close.svg" alt="close" @click="close"></button>
      </div>
    </section>
    </transition>
  </teleport>
</template>

<script setup>
import { defineEmits, defineProps } from 'vue'
defineProps({
  isOpen: Boolean
})
const emit = defineEmits(['close'])
const close = () => emit('close')
</script>

<style scoped>
  .modal{
    background: rgba(0, 0, 0, .3);
    position: fixed;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    display: grid;
    justify-content: center;
    align-items: center;
  }

  h3 {
    color: var(--brand-blue);
  }

  .modal__container{
    background: #FFF;
    min-height: 250px;
    min-width: 200px;
    position: relative;
    padding: 10px;
    border-radius: 12px;
  }

  button {
    position: absolute;
    width: 25px;
    height: 25px;
    top: -10px;
    right: -10px;
    background: #FFF;
    border-radius: 50%;
    padding: 5px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.3);
    border: none;
    outline: none;
    cursor: pointer;
  }

  button img {
    width: 100%;
  }

  .show-enter-active,
  .show-leave-active {
    transition: opacity .2s ease;
  }

  .show-enter-from,
  .show-leave-to {
    opacity: 0;
  }
</style>
