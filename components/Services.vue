<template>
  <div id="services" class="block float-left w-full pt-4 pb-16">
    <div class="block w-11/12 mx-auto my-8 text-center text-black">
      <div class="block w-full">
        <h2 class="block text-5xl font-bold pt-10">
          What We Do Best
        </h2>
      </div>
      <div class="grid grid-cols-1 gap-4 w-full mx-auto my-0 pt-16 text-center text-black md:w-9/12 md:grid-cols-3">

        <div class="p-4 text-center text-black" v-for="post in displayedPosts" :key="post.id">
          <h3 class="font-bold text-2xl mb-4">
            {{post.title.rendered}}
          </h3>
          <div class="row" v-html="post.content.rendered" />
        </div>

      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  data () {
    return {
      posts: [],
      // global variable set for consistent URL in main js
      page: 1,
      perPage: 10,
      pages: []
    }
  },
  // initial state methods
  methods: {
    // get posts
    getPosts () {
      axios
        .get(process.env.baseUrl + 'posts?per_page=10&categories=4')
        .then((response) => {
          this.posts = response.data
        })
        .catch((response) => {
          console.log(response)
        })
    },
    // set pages
    setPages () {
      const numberOfPages = Math.ceil(this.posts.length / this.perPage)
      for (let index = 1; index <= numberOfPages; index++) {
        this.pages.push(index)
      }
    },
    // paginate
    paginate (posts) {
      const page = this.page
      const perPage = this.perPage
      const from = page * perPage - perPage
      const to = page * perPage
      return posts.slice(from, to)
    }
  },
  // created
  created () {
    this.getPosts()
  },
  // watch
  watch: {
    posts () {
      this.setPages()
    }
  },
  // computed
  computed: {
    displayedPosts () {
      return this.paginate(this.posts)
    }
  }
}
</script>
