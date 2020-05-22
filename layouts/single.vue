<template>
  <!-- wrapper start -->
  <div id="app" class="block float-left width-full" :class="{'scrolled': scrollPosition, 'unscrolled': !scrollPosition}">
    <HeaderTwo />
    <nuxt />
  </div>
  <!-- wrapper end -->
</template>

<script>
import HeaderTwo from '~/components/HeaderTwo.vue'
export default {
  components: {
    HeaderTwo
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
