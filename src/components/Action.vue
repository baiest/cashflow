<template>
    <button @click="toogleModal">Agregar movimiento</button>
    <Modal :is-open="isOpenModal" @close="isOpenModal = false">
      <template #header>
        Nuevo Movimiento
      </template>
      <template #content>
        <Form @submit="submit"/>
      </template>
    </Modal>
</template>

<script setup>
import Modal from './Modal.vue'
import Form from './Form.vue'
import { ref } from 'vue'

const isOpenModal = ref(false)
const toogleModal = () => { isOpenModal.value = !isOpenModal.value }

const submit = (data) => {
  console.log(data)
  isOpenModal.value = false
}

</script>

<style>
  button {
    background: var(--brand-blue);
    color: #FFF;
    outline: none;
    border: none;
    padding: 10px 20px;
    border-radius: 25px;
    width: 250px;
    margin: 20px;
    cursor: pointer;
    font-size: 1.6rem;
    box-shadow: 0 4px 5px #ccc;
  }
</style>
