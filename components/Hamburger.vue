<template>
  <button :class="{'active': menuClose, 'inactive': !menuClose}" @click="clickHandler">
    <span class="bg-pink" />
    <span class="bg-pink" />
    <span class="bg-pink" />
  </button>
</template>
<script>
export default {
  props: {
    menuClose: Boolean
  },
  data () {
    return {}
  },
  methods: {
    clickHandler (e) {
      this.$emit('toggle')
    }
  }
}
</script>

<style scoped>
/* Hamburger */
button {
  display: block;
  float: right;
  background: none;
  outline: 0;
  border: 0;
  height: 26px;
  width: 46px;
  margin: 0;
  -webkit-transform: rotate(0deg);
  transform: rotate(0deg);
  transition: 0.5s ease-in-out;
  cursor: pointer;
}
button span {
  display: block;
  position: absolute;
  height: 2px;
  width: 100%;
  opacity: 1;
  left: 0;
  -webkit-transform: rotate(0deg);
  transform: rotate(0deg);
  transition: 0.25s ease-in-out;
}
button span:nth-child(1) {
  top: 0px;
}
button span:nth-child(2) {
  top: 13px;
}
button span:nth-child(3) {
  top: 26px;
}
.active button span:nth-child(1) {
  top: 13px;
  -webkit-transform: rotate(135deg);
  transform: rotate(135deg);
}
.active button span:nth-child(2) {
  opacity: 0;
  left: -50px;
}
.active button span:nth-child(3) {
  top: 13px;
  -webkit-transform: rotate(-135deg);
  transform: rotate(-135deg);
}
</style>
