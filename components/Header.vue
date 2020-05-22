<template>
  <div id="header-state" class="block" >
    <header class="block fixed z-50 w-full pt-1 pb-4">
      <div class="flex w-full mx-auto my-0 px-10 pt-3">
        <div class="flex-grow text-gray-700 w-0">
          <Icons />
        </div>
        <div class="flex-none w-8">
          <Icon />
        </div>
        <div class="flex flex-grow justify-end items-center w-0">
          <Nav />
        </div>
      </div>
    </header>
  </div>
</template>
<style>
#app #header-state header {
  background-color: transparent;
  transition: background-color ease 0.3s;
}
#app.scrolled #header-state header {
  background-color: theme('colors.white');
}
</style>

<script>
import Icons from '~/components/Icons.vue'
import Icon from '~/components/Icon.vue'
import Nav from '~/components/Nav.vue'
export default {
  components: {
    Icons,
    Icon,
    Nav
  }
}
</script>
