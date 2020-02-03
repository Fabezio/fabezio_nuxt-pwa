<template lang="pug">
v-app
  Navbar
  MoreInfo
  nuxt
  Footer

</template>

<script>
// import pdf from 'vue-pdf';
import Navbar from '@/components/Navbar'
import Footer from '@/components/Footer'
import MoreInfo from '@/components/MoreInfo.vue'
export default {
  components: {
    Navbar,
    MoreInfo,
    Footer
  }
}
</script>

<style></style>
