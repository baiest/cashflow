<template>
  <section class="movements">
    <div class="head" @click="toogleIsShow">
      <span class="grip"></span>
    </div>
    <h2 class="title">Historial</h2>
    <div class="body" v-show="isShow">
      <MovementCard v-for="item in movements" :key="item.id"
        :title="item.title"
        :description="item.description"
        :amount="item.amount"
        @remove="remove"
      />
    </div>
  </section>
</template>

<script>
import { ref } from 'vue'
import MovementCard from './MovementCard.vue'
export default {
  props: {
    movements: Array
  },
  components: {
    MovementCard
  },
  setup (props) {
    const isShow = ref(true)
    const toogleIsShow = () => {
      console.log('isShow')
      isShow.value = !isShow.value
    }

    const remove = (id) => {
      console.log('remove', id)
    }
    return {
      isShow,
      toogleIsShow,
      remove
    }
  }
}
</script>

<style scoped>
  .movements{
    padding: 10px;
  }
  .head {
    display: flex;
    justify-content: center;
    padding: 20px 10px;
    margin: 10px;
    cursor: pointer;
  }

  .head .grip {
    background: #ccc;
    height: 8px;
    width: 30%;
    border-radius: 20px;
  }

  .title {
    margin: 10px 0;
    font-size: 2.5rem;
    color: var(--brand-blue);
  }

  .body {
    margin: 20px 10px;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
</style>
