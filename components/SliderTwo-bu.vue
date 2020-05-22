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
    <hooper
      :hover-pause="false"
      :wheel-control="false"
      :auto-play="true"
      :play-speed="8000"
      :transition="600"
      :center-mode="true"
      :vertical="true"
    >
      <slide>
        <div class="block w-full">
          <div class="block w-11/12 mx-auto my-0 text-center text-white md:w-6/12">
            <p class="italic text-xl">
              Hurrah Marketing launched a digital strategy for us including web and social platforms. From the start they have done an incredible job and been a pleasure to work with. We look forward to keep working with them as they keep delivering the results!
            </p>
          </div>
        </div>
      </slide>
      <slide>
        <div class="block w-full">
          <div class="block w-11/12 mx-auto my-0 text-center text-white md:w-6/12">
            <p class="italic text-xl">
              Creativity at its best! From a new brand to marketing strategy they are truly ingenious with how they made our business stand out. Highly recommended.
            </p>
          </div>
        </div>
      </slide>
      <slide>
        <div class="block w-full">
          <div class="block w-11/12 mx-auto my-0 text-center text-white md:w-6/12">
            <p class="italic text-xl">
              Hurrah have demonstrated to us the power of a good social media. Our business is growing daily
            </p>
          </div>
        </div>
      </slide>
    </hooper>
  </div>
</template>

<script>
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
.hooper,
.hooper-track,
.hooper-list,
.hooper ul,
.hooper li{
  height: 300px;
}

.hooper li {
  color: #fff;
  display: block;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
