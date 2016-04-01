<template>

  <div class="box-container" v-bind:class="{'active':active}">

    <h2 class="title">{{ title }}</h2>
    <p>Messages: {{ messages | json}}</p>
    
    <!-- <component-child 
      v-for="item in list"
      v-bind:item="item"
    ></component-child> -->

    <ul class="list">
      <li v-for="item in list">
        <img v-bind:src="item.faceurl" width="32" height="32" alt="">
        <h3>{{ item.username }}</h3>
        <p>{{ item.content }}</p>
      </li>
    </ul>  

  </div> 

</template>

<script>
var Vue = require('vue')
var VueResource = require('vue-resource')

Vue.use(VueResource)

export default {
  http: {
    root: 'http://test.magapp.cc',
    headers: {
      Authorization: 'Basic YXBpOnBhc3N3b3Jk'
    },
    emulateJSON: true
  },
  data () {
    return {
      active: true,
      title: 'This is box componment',
      messages: [],
      list: []
    }
  },
  components: {
    ComponentChild: {
      template: '<p><input type="text" class="control" v-model="msg"></p><button class="btn-notify" v-on:click="notify">dispatch event</button><div>{{ item.username }}--打赏的时候说--{{ item.content }}</div>',
      data () {
        return {
          msg: 'child kit'
        }
      },
      methods: {
        notify () {
          if (this.msg.trim()) {
            this.$dispatch('changeParentMsg', this.msg)
            this.msg = ''
          }
        }
      }
    }
  },
  events: {
    changeParentMsg (msg) {
      this.messages.push(msg)
    }
  },
  ready () {
    this.$http.get('http://test.magapp.cc/pro_index_groupdetail', {id: '845m2'}).then(function (res) {
      this.$data.list = res.data.list.reward.rewardlist
    }, function (err) {
      console.log(err)
    })
  }
}
</script>

<style>
  .box-container{ line-height: 1.6;}
  .box-container.active{ color:#a1323e; }
  .box-container h2{ margin-bottom: 12px;}  
  .btn-notify{ height:32px; font-size: 14px; margin: 12px 0;}  
  </style>

  <style scoped>
  .title{ color:#999; }
</style>