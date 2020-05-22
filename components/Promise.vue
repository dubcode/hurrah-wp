<template>
  <div id="promise" class="block float-left w-full">
    <div class="block w-11/12 mx-auto my-0 py-16 text-center text-white md:w-6/12">
      <h2 class="text-5xl font-bold">
        {{promise_title}}
      </h2>
      <div class="text-lg" v-html="this.promise_excerpt" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  // post data
  data () {
    return {
      id: this.$route.params.id,
      baseUrl: process.env.baseUrl + 'pages/8?_embed',
      // global variable set for consistent URL in main js
      posts: [],
      post: '',
      promise_title: '',
      promise_excerpt: ''
    }
  },
  mounted () {
    this.getSingle()
    window.removeEventListener('scroll', this.onScroll)
  },
  // post methods
  methods: {
    // get single post
    getSingle () {
      this.id = this.$route.params.id
      axios.get(this.baseUrl, {
      })
        .then((response) => {
          this.promise_title = response.data.acf.promise_title
          this.promise_excerpt = response.data.acf.promise_excerpt
        })
        .catch((response) => {
          // response
        })
    }
  }
}
</script>

<style scoped>
#promise {
  background: url('/ptn.gif') repeat 0 0;
}
</style>
