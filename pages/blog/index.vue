<template>
  <div class="block float-left w-full pt-8">
    <div class="block float-left w-full py-16 text-black text-center mb-16">
      <h6 class="text-5xl font-bold">Give your business a reason to smile!</h6>
      <p class="text-lg">Read our latest articles</p>
    </div>
    <div class="block float-left w-full">

      <div class="block w-11/12 xl:w-8/12 mx-auto my-0">

        <!--col1-->
        <div class="block float-left w-full md:pr-8 md:border-r md:border-lgrey md:w-8/12">
          <router-link :to="{ path: '/blog/'+ post.id +'/' + post.slug}" class="cell block float-left w-full mb-12" v-for="post in displayedPosts" :key="post.id">
              <div class="block float-left w-full mb-4">
                  <h4 class="text-3xl font-bold text-black" v-html="post.title.rendered" />
                  <p class="text-sm mb-4 font-bold text-grey" v-html="post.date.substring(0,10)" />
                  <img class="block float-left h-auto w-full" :src="post.images.medium" alt="post.title.rendered" />
              </div>
              <div class="block float-left bg-pink border border-solid border-pink font-semibold text-white text-center py-4 px-8 duration-300 hover:bg-grey hover:border-grey">
                read more
              </div>
          </router-link>
          <div class="block float-left w-full pb-24">
            <button class="block float-left bg-grey px-2 py-1 text-baby font-bold mr-1 hover:bg-black duration-300" type="button" v-if="page != 1" @click="page--"> prev </button>
            <button class="block float-left bg-grey px-2 py-1 text-baby font-bold mr-1 hover:bg-black duration-300" type="button" v-for="pageNumber in pages.slice(page-1, page+5)" :key="pageNumber" @click="page = pageNumber"> {{pageNumber}} </button>
            <button class="block float-left bg-grey px-2 py-1 text-baby font-bold mr-1 hover:bg-black duration-300" type="button" @click="page++" v-if="page < pages.length"> next </button>
          </div>
        </div>
        <!--col1-->

        <!--col2-->
        <div class="hidden md:float-left md:w-4/12 md:pl-8 md:block">

          <div class="block float-left w-full mb-12">
            <h3 class="bg-pink block float-left w-full text-center mb-4 px-4 py-3 uppercase text-white text-lg font-semibold">Latest blog posts</h3>
            <router-link :to="{ path: '/blog/'+ post.id +'/' + post.slug}" class="block float-left w-full" v-for="post in displayedPosts" :key="post.id">
              <div class="block float-left w-full">
                  <h4 class="text-lg text-grey mb-4 duration-300 hover:text-pink" v-html="post.title.rendered" />
              </div>
            </router-link>
          </div>

          <!--
          <div class="block float-left w-full mb-12">
            <h3 class="bg-pink block float-left w-full text-center mb-4 px-4 py-3 uppercase text-white text-lg font-semibold">Sign up today</h3>
            <p class="text-lg text-grey">To receive regular updates direct to your inbox.</p>
          </div>
          -->

        </div>
        <!--col2-->
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
</style>
