<template>
  <div id="app">
    <img class="logo" src="./assets/logo.png">
    <a href="###" class="demo-link">这是一个测试Less的链接</a>
    <div class="demo-router">
      <a v-link="{ path: '/foo' }">Go to Foo</a>
      <a v-link="{ path: '/bar' }">Go to Bar</a>
    </div>
    <div class="main-body cf">
      <div class="aside">
        <hello></hello>
      </div>
      <div class="section">
        <box></box>
      </div>
    </div>
    <div class="intro-info">
      <p>
        Welcome to your Vue.js app. To get started, take a look at the
        <a href="https://github.com/vuejs-templates/webpack#folder-structure" target="_blank">README</a>
        of this template. If you have any issues with the setup, please file an issue at this template's repository.
      </p>
      <p>
        For advanced configurations, checkout the docs for
        <a href="http://webpack.github.io/" target="_blank">Webpack</a> and
        <a href="http://vuejs.github.io/vue-loader/" target="_blank">vue-loader</a>.
      </p>
      <p>
        You may also want to checkout
        <a href="https://github.com/vuejs/vue-router/" target="_blank">vue-router</a> for routing and
        <a href="https://github.com/vuejs/vuex/" target="_blank">vuex</a> for state management.
      </p>
    </div>
  </div>
</template> 

<script>
import Hello from './components/Hello'
import Box from './components/Box'

export default {
  components: {
    Hello,
    Box
  }
}
</script>

<style lang="less">
@import './assets/less/variables.less';

.demo-link{ font-size: 16px; color: @theme-color; }
.main-body{ width: 960px; margin: 0 auto; }
.aside{ width: 640px; float: left; margin-right: 12px; }
.section{ overflow: hidden; }

#app { font-family: Helvetica, sans-serif; padding: 32px; color: @gray-dark;}

.logo { display: block; margin:0 auto 30px auto; width: 100px; }
</style>
