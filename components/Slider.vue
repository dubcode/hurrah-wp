<template>
<div id="slide_one" class="block float-left h-full w-full">
  <hooper
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
</div>
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
#slide_one .hooper{
  height: 80vh;
}
#slide_one .hooper-list,
#slide_one .hooper-track,
#slide_one .hooper-slide{
  height: 100%;
  width: 100%;
}
#slide_one .hooper-slide{
  display: flex;
  align-items: center;
  justify-content: center;
}
#slide_one .hooper img {
  display: block;
  height: auto;
  margin: 0 auto;
  width: 100%;
  max-width: 1024px;
}
</style>
