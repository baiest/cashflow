<template>
  <div class="container">
    <p class="label">{{ label }}</p>
    <h2 class="amount">{{ amountCurrency }}</h2>
    <div class="graphic">
      <slot name="graphic"></slot>
    </div>
    <div class="action">
      <slot name="action"></slot>
    </div>
  </div>
</template>

<script>
import { currencyFormatter } from '@/utils/currency'
import { computed, toRefs } from 'vue'

export default {
  props: {
    label: String,
    amount: Number
  },
  setup (props) {
    const { amount } = toRefs(props)
    const amountCurrency = computed(() => currencyFormatter.format(amount.value))
    return {
      amountCurrency
    }
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
