<template>
  <div class="container">
    <p class="label">{{ label }}</p>
    <h2 class="amount">{{ amount }}</h2>
  </div>
</template>

<script>

export default {
  props: {
    label: String,
    amount: Number
  },
  setup () {

  }
}

</script>

<style scoped>
  .container {
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .label {
    color: #8e8eAF;
    margin: 5px;
  }

  .amount {
    color: var(--brand-green);
    margin: 5px;
  }
</style>
