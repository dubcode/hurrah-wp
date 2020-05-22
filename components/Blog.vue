<template>
  <div id="blog" class="block float-left w-full pt-8">
    <div class="block float-left w-full py-16 text-black text-center mb-16">
      <h6 class="text-5xl font-bold">Go on, let us give your business a reason to smile</h6>
      <p class="text-lg">Read our latest articles</p>
    </div>
    <div class="grid grid-cols-1 gap-4 w-10/12 mx-auto my-0 md:grid-cols-2 lg:grid-cols-4">
      <router-link :to="{ path: '/blog/'+ post.id +'/' + post.slug}" class="cell block h-64 bg-center bg-cover" :style="{ backgroundImage: `url( ${post.images.medium})`}" v-for="post in displayedPosts" :key="post.id">
          <div class="h-full w-full relative">
            <div class="bg-block block h-full w-full opacity-75 absolute z-0 duration-300" />
            <div class="flex items-center justify-center text-center text-white h-full w-full absolute z-10">
              <div class="block w-full p-8">
                <h4 class="text-xl font-bold" v-html="post.title.rendered" />
                <p class="text-sm" v-html="post.date.substring(0,10)" />
              </div>
            </div>
          </div>
      </router-link>
      <div class="block float-left w-full pb-24">
        <button class="block float-left bg-grey px-2 py-1 text-baby font-bold mr-1 hover:bg-black duration-300" type="button" v-if="page != 1" @click="page--"> prev </button>
        <button class="block float-left bg-grey px-2 py-1 text-baby font-bold mr-1 hover:bg-black duration-300" type="button" v-for="pageNumber in pages.slice(page-1, page+5)" :key="pageNumber" @click="page = pageNumber"> {{pageNumber}} </button>
        <button class="block float-left bg-grey px-2 py-1 text-baby font-bold mr-1 hover:bg-black duration-300" type="button" @click="page++" v-if="page < pages.length"> next </button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  layout: 'layout-two',
  data () {
    return {
      posts: [],
      // global variable set for consistent URL in main js
      page: 1,
      perPage: 8,
      pages: []
    }
  },
  // initial state methods
  methods: {
    // get posts
    getPosts () {
      axios
        .get(process.env.baseUrl + 'posts?per_page=100&categories=1')
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
