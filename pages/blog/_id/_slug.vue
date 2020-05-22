<template>
  <div class="block float-left w-full pt-32">
    <div class="block text-black mx-auto my-0 w-10/12">
        <h4 class="text-4xl font-bold text-center mx-auto my-0 w-8/12 md:w-6/12" v-html="this.title" />
        <p class="text-sm text-center pb-16" v-html="this.date.substring(0,10)" />
        <div class="content block float-left w-full" v-html="this.content" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {

  // meta
  head () {
    return {
      title: this.title,
      bodyAttrs: { class: 'single' },
      meta: [
        { hid: 'description', name: 'description', content: this.excerpt },
        { hid: 'og:title', name: 'og:title', content: this.title },
        { hid: 'og:description', name: 'og:description', content: this.excerpt }
      ]
    }
  },

  // post data
  data () {
    return {
      id: this.$route.params.id,
      // global variable set for consistent URL in main js
      posts: [],
      post: '',
      title: '',
      thumb: '',
      content: '',
      date: '',
      categoryId: '',
      tags: '',
      isActive: 'isActive'
    }
  },
  // post methods
  methods: {
  // get single post
    getSingle () {
      this.id = this.$route.params.id
      axios.get(process.env.baseUrl + 'posts/' + this.id + '?_embed', {
      })
        .then((response) => {
          this.title = response.data.title.rendered
          this.content = response.data.content.rendered
          this.thumb = response.data.images.medium
          this.tags = response.data.tags
          this.date = response.data.date
          this.categoryId = response.data.categories[0]
        })
        .catch((response) => {
          console.log(response)
        })
    }
  },
  mounted () {
    this.getSingle()
  }
}
</script>
