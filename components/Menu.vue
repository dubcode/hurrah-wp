<template>
  <div id="menu" class="block flex justify-center items-center h-full w-full p-4 bg-white duration-300 fixed z-40">
    <ul class="w-full">
      <li class="inline-block mr-6">
        <a href="/" class="text-xs text-pink font-semibold uppercase hover:text-grey">Home</a>
      </li>
      <li class="inline-block mr-6">
        <a href="/blog" class="text-xs text-pink font-semibold uppercase hover:text-grey">Blog</a>
      </li>
    </ul>
  </div>
</template>

<style scoped>
#header-state.inactive #menu {
  opacity: 0;
  pointer-events:none;
}
#header-state.active #menu {
  opacity: 1;
  pointer-events: all;
}
</style>
