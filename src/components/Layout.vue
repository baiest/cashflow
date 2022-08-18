<template>
  <div  class="layout">
    <slot name="header"></slot>
    <main class="resume">
      <slot name="resume"></slot>
    </main>
    <footer class="movements">
      <slot name="movements"></slot>
    </footer>
  </div>
</template>

<script>
</script>

<style scoped>
  .layout {
    display: flex;
    flex-direction: column;
    height: 100vh;
  }
  .resume {
    margin: 0;
    position: relative;
    height: 100%;
  }
  .movements {
    width: 100%;
    background: #FFF;
    border-top-left-radius: 20px;
    border-top-right-radius: 20px;
    box-shadow: 0 -2px 8px rgba(0, 0, 0, .3);
    position: fixed;
    bottom: 0;
  }
</style>
