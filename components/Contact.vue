<template>
  <div id="contact" class="bg-black block float-left w-full">
    <div class="block w-11/12 mx-auto my-0 py-16 text-center text-white md:w-6/12">
      <h2 class="text-5xl font-bold">
        {{footer_title}}
      </h2>
      <p>
        <a class="hover:text-pink duration-300 text-lg" href="tel:07814932345" target="_blank">
          Telephone: 07814932345
        </a>
      </p>
      <p>
        <a class="hover:text-pink duration-300 text-lg" href="mailto:hello@hurrahmarketing.co.uk" target="_blank">
          Email: hello@hurrahmarketing.co.uk
        </a>
      </p>
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
      footer_title: ''
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
          this.footer_title = response.data.acf.footer_title
        })
        .catch((response) => {
          // response
        })
    }
  }
}
</script>
