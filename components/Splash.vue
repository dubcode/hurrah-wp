<template>
  <div id="splash" class="block flex items-center w-full h-screen overflow-hidden">
    <div class="flex items-center justify-center h-full w-full">
      <div class="block w-full">
        <div class="block w-full">
          <Logo />
        </div>
        <div class="block w-full text-black text-center text-5xl font-semibold">
          <h1 class="text-2xl md:text-5xl">
            Marketing . Design . Digital
          </h1>
        </div>
        <div class="block text-center py-8">
          <a v-scroll-to="'#portfolio'" href="#" class="bg-white70 border-2 border-solid border-pink font-semibold text-pink text-center mr-2 py-4 px-8 duration-300 hover:bg-pink hover:text-white">
            Our Work
          </a>
          <a v-scroll-to="'#contact'" href="#" class="bg-pink70 border border-solid border-pink70 font-semibold text-white text-center mr-2 py-4 px-8 duration-300 hover:bg-pink hover:border-pink hover:text-white">
            Contact Us
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
#splash {
  background: url('/bg.jpg') no-repeat center bottom;
  background-size: cover;
  background-attachment: fixed;
}

</style>

<script>
import Logo from '~/components/Logo.vue'
export default {
  components: {
    Logo
  }
}
</script>
