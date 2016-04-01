<template>
  <div id="app">
    <img class="logo" src="./assets/logo.png">
    <a href="###" class="demo-link">这是一个测试Less的链接</a>
    

    <label class="label" for="viewa">
      <input type="radio" id="viewa" value="viewa" v-model="currentView">view a
    </label>
    <label class="label" for="viewb">
      <input type="radio" id="viewb" value="viewb" v-model="currentView">view b
    </label>
    <component 
      :is="currentView"
      transition="fade"
      transition-mode="out-in">
    </component>
    
    <input type="text" class="control" v-model="message">
    <component-child v-bind:msg="message" :count="3">
      <h2></h2>
    </component-child>
    
    <ul class="demo-list">
      <component-listitem
        v-for="item in list"
        v-bind:item="item"
      ></component-listitem>
    </ul>

    <div class="main-body cf">
      <div class="aside">
        <component-hello></component-hello>
      </div>
      <div class="section">
        <component-box></component-box>
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
import ComponentHello from './components/Hello'
import ComponentBox from './components/Box'
import ComponentListitem from './components/list-item'

var Vue = require('vue')
var VueRouter = require('vue-router')

Vue.use(VueRouter)

var parentComponent

export default {
  created () {
    parentComponent = this
    console.log('this is app: ' + this.$parent)
    console.log('this is app: ' + this.$root)
    console.log(this.$root === this.$parent)
  },
  data () {
    return {
      currentView: 'viewa',
      message: 'this msg is from parent component',
      title: 'title shown in child component wrapped tags',
      list: [
        {
          username: 'zhouyuan',
          des: 'very handsome man'
        },
        {
          username: 'zhouyuan',
          des: 'very handsome man'
        },
        {
          username: 'zhouyuan',
          des: 'very handsome man'
        }
      ]
    }
  },
  components: {
    ComponentBox,
    ComponentHello,
    ComponentListitem,
    /* 自定义局部组件 */
    ComponentChild: {
      props: {
        count: Number,
        msg: {
          type: String,
          required: true
        }
      },
      template: '<div class="cmpt-child"><p class="child-msg">{{ msg }}</p><p class="child-msg">{{ count+1*8 }}</p><input type="text" class="control" v-model="msg"><slot><p>this is the slot tag wrapped content in child component</p></slot></div>',
      ready () {
        console.log(this.$parent === parentComponent)
        console.log(this.$root)
      }
    },
    viewa: {
      template: '<div class="transition-cmpt">This is view A</div>'
    },
    viewb: {
      template: '<div class="transition-cmpt">This is view B</div>'
    }
  }
}
</script>

<style lang="less">
  @import './assets/less/variables.less';

  #app{ width: 720px; margin: 0 auto; font-family: Helvetica, sans-serif; padding: 32px; color: @gray-dark;}

  .demo-link{ display: block; margin-bottom: 12px; font-size: 16px; color: @theme-color; }
  .aside{ width: 480px; float: left; margin:24px 12px 0 0; }
  .section{ overflow: hidden; }
  
  .label{ margin-right: 8px;}
  .transition-cmpt{ font-size: 16px; margin:8px 0 24px; }
  input[type="radio"]{ appearance:radio; }
  .fade-transition{ transition: opacity .3s ease; }
  .fade-enter, .fade-leave{ opacity: 0; }

  .logo { display: block; margin:0 auto 30px auto; width: 100px; }
  .child-msg{ margin:12px 0; }
</style>
