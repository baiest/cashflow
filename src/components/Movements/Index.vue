<template>
  <section class="movements">
    <div class="head" @click="toogleIsShow">
      <span class="grip"></span>
    </div>
    <h2 class="title">Historial</h2>
    <div class="body" v-show="isShow">
      <MovementCard v-for="item in movements" :key="item.id"
        :id="item.id"
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
  setup (_, ctx) {
    const isShow = ref(false)
    const toogleIsShow = () => {
      isShow.value = !isShow.value
    }

    const remove = (id) => {
      ctx.emit('remove', id)
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
    cursor: pointer;
    position: sticky;
    top: 0;
    left: 0;
    background: #FFF;
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
