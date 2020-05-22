<template>
  <!-- wrapper start -->
  <div id="app" :class="{'scrolled': scrollPosition, 'unscrolled': !scrollPosition}">
    <Header />
    <nuxt />
  </div>
  <!-- wrapper end -->
</template>

<script>
import Header from '~/components/Header.vue'
export default {
  components: {
    Header
  },
  data () {
    return {
      scrollPosition: null
    }
  },
  mounted () {
    window.addEventListener('scroll', this.updateScroll)
  },
  methods: {
    updateScroll () {
      this.scrollPosition = window.scrollY
    }
  }
}
</script>
<style>
*:focus,
button:focus  {outline:none;}
body {
  font-family: 'Montserrat', sans-serif;
}
</style>
