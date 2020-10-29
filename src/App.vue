<template>
  <div id="vonut" class="vonut">
    <navigator :showNav="showNav"></navigator>
    <main class="vonut-main">
      <transition :name="transitionName">
        <router-view class="vonut-main-view"></router-view>
      </transition>
    </main>
    <tags></tags>
	<footer class="footer sub">
		<div class="footer_social">
			<a href="https://twitter.com/th6688" target="_blank">Twitter</a>
			<a href="https://facebook.com/" target="_blank">Facebook</a>
			<a href="mailto:thuanvodka@gmail.com" target="_blank">Email</a>
		</div>
		<p class="footer_text">Copyright Mrthuan &copy 2020</p>
	</footer>
  </div>
</template>

<script>
import navigator from '~components/navigator'
import tags from '~components/tags'
export default {
  data () {
    return {
      nav: false,
      transitionName: '',
      showNav: true
    }
  },
  watch: {
    $route (to, from) {
      to.path === '/' ? this.transitionName = 'slide-left' : this.transitionName = 'slide-right'
    }
  },
  mounted () {
    const body = document.body
    body.onscroll = () => {
      if (body.scrollTop > 40) {
        this.showNav = false
      } else {
        this.showNav = true
      }
    }
  },
  components: {
    navigator,
    tags
  }
}
</script>

<style lang="less">
@transition: all ease .4s;
@import '~assets/style.less';
@import '~assets/markdown.less';
@import '~assets/transition.less';

.vonut {
  position: relative;
  min-height: 100%;
  overflow: scroll;
  padding-top: 40px;
  &-main {
    position: relative;
    max-width: 1024px;
    margin: 50px auto;
    box-sizing: border-box;
    display: flex;
    justify-content: center;
    &-view {
      transition: all ease .5s;
    }
    &> section {
      background: #fff;
      width: 100%;
      margin-top: 15px;
      padding: 15px;
      box-sizing: border-box;
      box-shadow: 0 3px 12px rgba(0, 0, 0, .3);
      p:first-child {
        display: none;
      }
      img {
        max-width: 100%;
      }
    }
  }
}
.footer{
    padding: 0.75rem;
    font-size: 15px;
    line-height: 1.5;
    color: #a5a5a5;
	border-top: 1px solid #c1c1c1;
	margin: 75px auto 20px auto;
    background: none!important;
    border-radius: 0!important;
    box-shadow: none!important;
}
.footer_social {
	display: flex;
    justify-content: center;
    padding: 0.5rem 0;
    width: 100%;
    flex-wrap: wrap;
}
.footer a {
  margin: 0.75rem;
}
.footer_text {
  margin: 0.5rem auto;
  white-space: nowrap;
  text-align: center;
}
</style>
