<template>
  <section ref="container" :class="{'movements-container': true, 'show-body': isShow}" >
    <div class="head" @click="toogleIsShow">
      <span class="grip"></span>
    </div>
    <h2 class="title">Historial</h2>
    <transition name="body">
      <div class="body" v-show="isShow">
        <MovementCard v-for="item in movements" :key="item.id"
          :id="item.id"
          :title="item.title"
          :description="item.description"
          :amount="item.amount"
          @remove="remove"
        />
      </div>
    </transition>
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
    const container = ref(null)
    const toogleIsShow = () => {
      isShow.value = !isShow.value
      if (isShow.value && container.value) {
        container.value.parentElement.classList.add('show-body')
      } else {
        container.value.parentElement.classList.remove('show-body')
      }
    }

    const remove = (id) => {
      ctx.emit('remove', id)
    }

    return {
      isShow,
      container,
      toogleIsShow,
      remove
    }
  }
}
</script>

<style scoped>
  .movements-container {
    padding: 10px;
    padding-top: 0;
    height: 100%;
    overflow: auto;
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

  .body-enter-active,
  .body-leave-active {
    transition: opacity .2s ease;
  }

  .body-enter-from,
  .body-leave-to {
    opacity: 0;
  }
</style>
