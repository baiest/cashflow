<template>
<section class="splashscreen">
  <img
    src="@/assets/cashflow.svg"
    alt="Logo CashFlow" />
  <h1><span>Cash</span>Flow</h1>
</section>
</template>

<style scoped>
  .splashscreen{
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }

  h1 {
    color: var(--brand-blue);
  }

  h1 span {
    color: var(--brand-green);
  }
</style>
