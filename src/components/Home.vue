<template>
  <Layout>
    <template #header>
      <Header />
    </template>
    <template #resume>
      <Resume />
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
export default {
  components: {
    Layout,
    Header,
    Resume,
    Movents
  }
}
</script>

<style scoped>

</style>
