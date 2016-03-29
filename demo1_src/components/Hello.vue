<template id="hello_mod">
  <div class="hello">
    <h1 class="title">{{ msg }}</h1>
    <ul class="cmt-list">
      <li v-for="item in list">
        <span>{{ item.username }}</span>
        <p  class="des" v-on:click="showIndex()" v-html="item.content"></p>
        <p>{{ item.pubdate }}</p>
      </li>
    </ul>
  </div>
</template>

<script>
var $ = require('jquery')

export default {
  data () {
    return {
      // note: changing this line won't causes changes
      // with hot-reload because the reloaded component
      // preserves its current state and we are modifying
      // its initial state.
      msg: 'Hello World! This is from hello componment',
      list: null
    }
  },
  created () {
    var _this = this
    $.ajax({
      url: 'http://test.magapp.cc/pro_index_groupdetail',
      data: {
        id: '845m2'
      },
      type: 'GET',
      dataType: 'json',
      success: function (data) {
        _this.$data.list = data.list.comment.newest
      },
      error: function (err) {
        console.log(err)
      }
    })
  },
  methods: {
    showIndex: function () {
      console.log('you click me')
    }
  }
}

</script>

<style lang="less">
@import '../assets/less/variables.less';

.title{ color:@theme-color;}
.cmt-list li{ padding: 10px 0; }
.cmt-list .des{ font-size: 14px; line-height: 1.6; }
.cmt-list .smile{ width:24px; vertical-align: text-bottom; }
</style>