<template>
  <hooper
    class="block float-left w-full"
    :hover-pause="false"
    :wheel-control="false"
    :auto-play="true"
    :play-speed="12000"
    :transition="600"
    :center-mode="true"
  >
    <slide>
      <img src="p1.jpg" alt="">
    </slide>
    <slide>
      <img src="p2.jpg" alt="">
    </slide>
    <slide>
      <img src="p3.jpg" alt="">
    </slide>
    <slide>
      <img src="p4.jpg" alt="">
    </slide>
    <slide>
      <img src="p5.jpg" alt="">
    </slide>
    <hooper-navigation slot="hooper-addons" />
  </hooper>
</template>

<script>
import {
  Hooper,
  Slide,
  Navigation as HooperNavigation
} from 'hooper'
import 'hooper/dist/hooper.css'

export default {
  name: 'App',
  components: {
    Hooper,
    Slide,
    HooperNavigation
  }
}
</script>

<style scoped>
.hooper{
  min-height: 80vh;
  justify-content: center;
  align-items: center;
}
.hooper li {
  display: block;
  text-align: center;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
.hooper img {
  display: block;
  height: auto;
  margin: 0 auto;
  width: 100%;
  max-width: 1024px;
}
</style>
