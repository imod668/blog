<template>
  <nav class="nav" :class="{'hide': !showNav}">
    <a href="index.html">Thuan's Blog</a>
    <a href="#" @click="twitterLink" target="_blank"><i class="fab fa-twitter"></i></a>
  </nav>
</template>

<script>
export default {
  props: [
    'showNav'
  ],
  methods: {
    twitterLink () {
      window.open('https://twitter.com/th6688')
    }
  }
}
</script>

<style lang="less">
.nav {
  position: fixed;
  top: 0;
  height: 50px;
  width: 100%;
  background: #42b983;
  padding: 0 15px;
  box-sizing: border-box;
  color: #fff;
  z-index: 9000;
  box-shadow: 0 3px 12px rgba(0, 0, 0, .2);
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: all ease .3s;
  h3 {
    margin: 0;
  }
  a{
	margin-right: 20px;
	color:#fff;
	text-decoration: none;
    font-size: 20px;
    font-weight: 600;
	line-height: 1px;
  }
  .fab {
    font-size: 24px;
  }
  &.hide {
    transform: translateY(-40px);
  }
}
</style>
