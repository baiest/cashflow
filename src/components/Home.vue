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
            <Action @create="create"/>
        </template>
      </Resume>
    </template>
    <template #movements>
      <Movements :movements="movements" @remove="remove"/>
    </template>
  </Layout>
</template>

<script>
import Layout from './Layout.vue'
import Header from './Header.vue'
import Resume from './Resume/Index.vue'
import Movements from './Movements/Index.vue'
import Action from './Action.vue'
import { computed, ref } from 'vue'
import Graphic from './Graphic.vue'
export default {
  components: {
    Layout,
    Header,
    Resume,
    Movements,
    Action,
    Graphic
  },
  setup () {
    const amountTotal = ref(15000)
    const amount = ref(15000)
    const labelByAmount = computed(() => amountTotal.value ? 'Ahorro Total' : '13/09/2022')
    const amountOrTotal = computed(() => amountTotal.value ? amountTotal.value : amount.value)
    const movements = ref([
      { id: 1, title: 'Titulo 1', date: new Date('2022-08-15'), description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: 10000 },
      { id: 3, title: 'Titulo 3', date: new Date('2022-08-16'), description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: -10000 },
      { id: 4, title: 'Titulo 4', date: new Date('2022-08-17'), description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: 10000 },
      { id: 5, title: 'Titulo 5', date: new Date('2022-08-18'), description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum aut mollitia facilis recusandae quod? Rem vero, dolorum voluptate labore ut recusandae voluptatem. Inventore ipsam deserunt pariatur voluptates, quaerat vitae animi?', amount: -10000 }
    ])
    const amounts = computed(() => {
      const lastDays = movements.value
        .filter(m => {
          const today = new Date()
          const oldDate = today.setDate(today.getDate() - 30)
          console.log(today, oldDate, m.date)
          return m.date >= oldDate
        })
        .map(m => m.amount)

      return lastDays.map((_, i) => {
        const lastMovements = lastDays.slice(0, i)
        return lastMovements.reduce((sum, m) => sum + m, 0)
      })
    })

    const create = (data) => {
      movements.value = [...movements.value, { ...data, id: movements.value[movements.value.length - 1].id + 1 }]
    }

    const remove = (id) => {
      movements.value = movements.value.filter(m => m.id !== id)
    }
    return {
      labelByAmount,
      amountOrTotal,
      movements,
      amounts,
      create,
      remove
    }
  }
}
</script>

<style scoped>

</style>
