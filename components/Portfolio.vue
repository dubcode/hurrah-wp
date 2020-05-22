<template>
  <div id="portfolio" class="block float-left w-full">
    <div class="block w-11/12 mx-auto my-0 pt-16 text-center text-black md:w-6/12">
      <h2 class="text-5xl font-bold">
        {{this.portfolio_title}}
      </h2>
      <p class="text-lg">
        {{this.portfolio_excerpt}}
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      id: this.$route.params.id,
      baseUrl: process.env.baseUrl + 'pages/8?_embed',
      posts: [],
      post: '',
      portfolio_title: '',
      portfolio_excerpt: ''
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
          this.portfolio_title = response.data.acf.portfolio_title
          this.portfolio_excerpt = response.data.acf.portfolio_excerpt
        })
        .catch((response) => {
          // response
        })
    }
  }
}
</script>
