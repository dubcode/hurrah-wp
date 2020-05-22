<template>
  <div id="header-state" class="block" :class="{'active': menuClose, 'inactive': !menuClose}">
    <header class="block fixed z-50 w-full pt-1 pb-4" :class="{'active': menuClose, 'inactive': !menuClose}">
      <div class="flex w-full mx-auto my-0 px-10 pt-3">
        <div class="flex-grow text-gray-700 w-0">
          <Icons />
        </div>
        <div class="flex-none w-8">
          <IconThree />
        </div>
        <div class="flex flex-grow justify-end items-center w-0">
          <NavTwo />
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
import IconThree from '~/components/IconThree.vue'
import NavTwo from '~/components/NavTwo.vue'
export default {
  components: {
    Icons,
    IconThree,
    NavTwo
  },
  props: {
    menuClose: Boolean
  }
}
</script>
