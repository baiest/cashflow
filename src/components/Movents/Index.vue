<template>
  <section class="movements">
    <div class="head" @click="toogleIsShow()">
      <span class="grip"></span>
    </div>
    <div class="body" v-show="isShow">
      hola
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const isShow = ref(false)
const toogleIsShow = () => {
  console.log(isShow.value)
  isShow.value = !isShow.value
}
</script>

<style scoped>
  .movements{

  }
  .head {
    display: flex;
    justify-content: center;
    padding: 20px 10px;
    margin: 10px;
  }

  .head .grip {
    background: #ccc;
    height: 8px;
    width: 30%;
    border-radius: 20px;
  }

  .body {
    margin: 20px 10px;
  }
</style>
