<template>
    <div id="testimonials" class="block float-left w-full pt-10">
      <div class="w-full items-center justify-center pt-10">
        <div class="my-0 mx-auto w-11/12 md:w-6/12">
          <h3 class="w-full text-center text-5xl font-bold text-white">
            Don’t just take our word for it!
          </h3>
          <div class="flex w-full items-center justify-center pt-10">
            <IconTwo />
          </div>
        </div>
      </div>
    <div id="slide_two" class="block float-left h-full w-full">
      <hooper
        :hover-pause="false"
        :wheel-control="false"
        :auto-play="true"
        :play-speed="8000"
        :transition="600"
        :center-mode="true"
        :itemsToShow="1"
      >
        <slide v-for="post in displayedPosts" :key="post.id">
          <div class="row">
            <div class="col">
              <div class="italic text-xl" v-html="post.content.rendered" />
            </div>
          </div>
        </slide>
      </hooper>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import {
  Hooper,
  Slide
} from 'hooper'
import 'hooper/dist/hooper.css'
import IconTwo from '~/components/IconTwo.vue'

export default {
  name: 'App',
  components: {
    IconTwo,
    Hooper,
    Slide
  },
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
        .get(process.env.baseUrl + 'posts?per_page=10&categories=3')
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
#testimonials {
  background: url('/bg2.jpg') no-repeat center center;
  background-size: cover;
  background-attachment: fixed;
  display: block;
  float: left;
  width: 100%;
}
#slide_two .hooper{
  height: 300px;
}
#slide_two .hooper-list,
#slide_two .hooper-track,
#slide_two .hooper-slide{
  height: 100%;
  width: 100%;
}

#slide_two .hooper li {
  color: #fff;
  display: block;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
}

#slide_two .row {
  display: block;
  width: 100%;
}
#slide_two .col {
  display: block;
  margin: 0 auto;
  text-align: center;
  color: theme('colors.white');
  width: 91.666667%;
}
#slide_two p:before {
    content: "\201C";
}

#slide_two p:after {
    content: "\201D";
}

@media only screen and (min-width: 1024px) {
#slide_two .col {
  width: 50%;
  }
}
</style>
