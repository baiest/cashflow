<template>
  <form @submit.prevent="onSubmit">
    <fieldset>
      <label for="title">Título</label>
      <input type="text" name="title" v-model="form.title">
    </fieldset>
    <fieldset>
      <label for="title">Monto</label>
      <input type="number" name="amount" v-model="form.amount">
    </fieldset>
    <fieldset>
      <label for="description">Descripcion</label>
      <textarea name="title" v-model="form.description" />
    </fieldset>
    <fieldset>
      <label>
        <input type="radio" v-model="form.movementType" value="ingreso" name="movementType">
        Ingreso
      </label>
      <label>
        <input type="radio" v-model="form.movementType" value="gasto" name="movementType">
        Gasto
      </label>
    </fieldset>
    <section>
      <button>Agregar movimiento</button>
    </section>
  </form>
</template>

<script setup>
import { reactive, defineEmits } from 'vue'

const form = reactive({
  title: '',
  amount: null,
  description: '',
  movementType: 'ingreso'
})

const emit = defineEmits(['submit'])

const onSubmit = () => {
  emit('submit', { ...form })
}
</script>

<style scoped>

  form {
    width: 300px;
  }

  fieldset {
    border: none;
    display: flex;
    flex-direction: column;
    gap: 5px;
  }

  input, textarea {
    border: 1px solid var(--brand-blue);
    border-radius: 8px;
    padding: 5px 10px;
  }

  input[type="number"]{
    text-align: right;
  }

  input::selection,
  textarea::selection {
    background: var(--brand-blue);
    color: #FFF;
  }

  input:focus-visible,
  textarea:focus-visible  {
    outline: 2px solid yellow;
    border-color: black;
  }
  section {
    text-align: center;
  }
</style>
