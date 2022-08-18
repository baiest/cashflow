<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume
        :label="labelByAmount"
        :amount="amountOrTotal"
      >
        <template #graphic>
            graphic
        </template>
        <template #action>
            action
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movents />
    </template>
  </Layout>
</template>

<script>
import Layout from './Layout.vue'
import Header from './Header.vue'
import Resume from './Resume/Index.vue'
import Movents from './Movents/Index.vue'
import { computed, ref } from 'vue'
export default {
  components: {
    Layout,
    Header,
    Resume,
    Movents
  },
  setup () {
    const amountTotal = ref(null)
    const amount = ref(0)
    const labelByAmount = computed(() => amountTotal.value ? 'Ahorro Total' : '13/09/2022')
    const amountOrTotal = computed(() => amountTotal.value ? amountTotal.value : amount.value)
    return {
      labelByAmount,
      amountOrTotal
    }
  }
}
</script>

<style scoped>

</style>
