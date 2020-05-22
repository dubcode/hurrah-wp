<template>
  <div id="about" class="bg-grey block float-left w-full">
    <div class="block w-11/12 mx-auto my-0 py-16 text-center text-white md:w-6/12">
      <h2 class="text-5xl font-bold">
        We are <LogoWhite />
      </h2>
      <p class="text-lg">
        {{this.intro_text}}
      </p>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import LogoWhite from '~/components/LogoWhite.vue'
export default {
  components: {
    LogoWhite
  },
  // post data
  data () {
    return {
      id: this.$route.params.id,
      baseUrl: process.env.baseUrl + 'pages/8?_embed',
      // global variable set for consistent URL in main js
      posts: [],
      post: '',
      intro_text: ''
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
          this.intro_text = response.data.acf.intro_text
        })
        .catch((response) => {
          // response
        })
    }
  }
}
</script>
