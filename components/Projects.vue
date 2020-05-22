<template>
  <div id="projects" class="block float-left w-full pt-8">
    <div class="grid grid-cols-1 w-10/12 mx-auto my-0 md:grid-cols-2 lg:grid-cols-4">
      <div class="cell block h-64 bg-center bg-cover" v-for="post in displayedPosts" :key="post.id">
          <div class="h-full w-full relative">
            <div class="bg-block block h-full w-full opacity-75 absolute z-0 duration-300" />
            <div class="flex items-center justify-center text-center text-white h-full w-full absolute z-10">
              <div class="block w-full">
                  <img :src="post.images.medium" :alt="post.title.rendered" />
              </div>
            </div>
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
        .get(process.env.baseUrl + 'posts?per_page=10&categories=2')
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

<style scoped>
.grid a:nth-child(1) .bg-block,
.grid a:nth-child(8) .bg-block {
  background-color: theme('colors.pink');
}
.grid a:nth-child(2) .bg-block,
.grid a:nth-child(7) .bg-block {
  background-color: theme('colors.orange');
}
.grid a:nth-child(3) .bg-block,
.grid a:nth-child(6) .bg-block {
  background-color: theme('colors.grey');
}
.grid a:nth-child(4) .bg-block,
.grid a:nth-child(5) .bg-block  {
  background-color: theme('colors.black');
}
.cell:hover .bg-block{
    opacity: 1;
}
</style>
