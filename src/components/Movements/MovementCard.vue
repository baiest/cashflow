<template>
  <div class="card">
    <div class="card-left">
      <h5 class="card__title">{{ title }}</h5>
      <p class="card__description">{{ description }}</p>
    </div>
    <div class="card-right">
      <span><img src="@/assets/trash.svg" alt="Trash" @click="remove(id)"></span>
      <span :class="{ 'red': isNegative, 'green': !isNegative }" class="card__amount">{{ amountCurrency }}</span>
    </div>
  </div>
</template>

<script setup>
import { currencyFormatter } from '@/utils/currency'
import { computed } from '@vue/reactivity'
import { defineProps, defineEmits, toRefs } from 'vue'
const props = defineProps({
  id: Number,
  title: String,
  description: String,
  amount: Number
})

const {
  id,
  title,
  description,
  amount
} = toRefs(props)

const amountCurrency = computed(() => currencyFormatter.format(amount.value))
const isNegative = computed(() => amount.value < 0)
const emit = defineEmits(['remove'])

const remove = (idMovement) => {
  emit('remove', idMovement)
}
</script>

<style>
  .card {
    background: lightcyan;
    padding: 20px;
    display: flex;
    justify-content: space-between;
    gap: 10px;
    border-radius: 12px;
    color: #4c4c4c;
  }

  .card-right{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: flex-end;
  }
  .card__title{
    margin: 5px 0;
    font-size: 2rem;
  }
  .card__description {
    max-height: calc(3 * 1.8rem);
    overflow: hidden;
    text-overflow: ellipsis;
  }

  .card__amount {
    font-size: 2rem;
  }
  .green {
    color: green;
  }

  .red {
    color: red;
  }
</style>
