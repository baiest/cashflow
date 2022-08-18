<template>
  <header class="header">
    <img @click="reload" src="@/assets/cashflow.svg" alt="Logo CashFlow" />
    <h1 class="header__title"><span>Cash</span>Flow</h1>
    <span></span>
  </header>
</template>

<script setup>
const reload = () => location.reload()
</script>

<style scoped>
  .header {
    display: flex;
    padding: 5px 10px;
    align-items: center;
    justify-content: space-around;
    height: 70px;
  }

  .header img {
    height: 100%;
    width: auto;
    object-fit: contain;
  }

  .header__title {
    font-size: 1.4rem;
    color: var(--brand-blue);
  }

  .header__title span {
    color: var(--brand-green);
  }
</style>
