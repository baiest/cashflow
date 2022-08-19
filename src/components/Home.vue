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
            <Graphic :amounts="amounts" />
        </template>
        <template #action>
            <Action />
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movents :movements="movements"/>
    </template>
  </Layout>
</template>

<script>
import Layout from './Layout.vue'
import Header from './Header.vue'
import Resume from './Resume/Index.vue'
import Movents from './Movements/Index.vue'
import Action from './Action.vue'
import { computed, ref } from 'vue'
import Graphic from './Graphic.vue'
export default {
  components: {
    Layout,
    Header,
    Resume,
    Movents,
    Action,
    Graphic
  },
  setup () {
    const amountTotal = ref(15000)
    const amount = ref(15000)
    const labelByAmount = computed(() => amountTotal.value ? 'Ahorro Total' : '13/09/2022')
    const amountOrTotal = computed(() => amountTotal.value ? amountTotal.value : amount.value)
    const amounts = [100, 200, 300, 400]
    const movements = [
      { id: 1, title: 'Titulo 1', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: 10000 },
      { id: 3, title: 'Titulo 3', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: -10000 },
      { id: 4, title: 'Titulo 4', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: 10000 },
      { id: 5, title: 'Titulo 5', description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: -10000 }
    ]

    return {
      labelByAmount,
      amountOrTotal,
      movements,
      amounts
    }
  }
}
</script>

<style scoped>

</style>
