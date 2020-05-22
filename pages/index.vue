<template>
  <!-- wrapper start -->
  <div id="app" class="block">
    <Splash />
    <About />
    <Portfolio />
    <Projects />
    <SliderTwo />
    <Services />
    <Promise />
    <Blog />
    <Contact />
  </div>
  <!-- wrapper end -->
</template>

<script>
import Splash from '~/components/Splash.vue'
import About from '~/components/About.vue'
import Portfolio from '~/components/Portfolio.vue'
import Projects from '~/components/Projects.vue'
import SliderTwo from '~/components/SliderTwo.vue'
import Services from '~/components/Services.vue'
import Promise from '~/components/Promise.vue'
import Blog from '~/components/Blog.vue'
import Contact from '~/components/Contact.vue'
export default {
  components: {
    Splash,
    About,
    Portfolio,
    Projects,
    SliderTwo,
    Services,
    Promise,
    Blog,
    Contact
  }
}
</script>
