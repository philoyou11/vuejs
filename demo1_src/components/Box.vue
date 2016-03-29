<template>
  <div class="box-container" v-bind:class="{'active':active}">
    <h2 class="title">{{ title }}</h2>
    <ul class="list">
      <li v-for="item in list">
        <h3>{{ item.name }}</h3>
        <p>{{ item.des }}</p>
      </li>
    </ul>  
  </div> 
</template>

<script>
export default {
  data () {
    return {
      active: true,
      title: 'This is box componment',
      list: [
        {
          name: '这是名字名字哦哦',
          des: '这里是描述哦哦哦'
        },
        {
          name: '这是名字名字哦哦',
          des: '这里是描述哦哦哦'
        },
        {
          name: '这是名字名字哦哦',
          des: '这里是描述哦哦哦'
        },
        {
          name: '这是名字名字哦哦',
          des: '这里是描述哦哦哦'
        },
        {
          name: '这是名字名字哦哦',
          des: '这里是描述哦哦哦'
        },
        {
          name: '这是名字名字哦哦',
          des: '这里是描述哦哦哦'
        }
      ]
    }
  }
}
</script>

<style scoped>
.title{ color:#999; }

.box-container{ line-height: 1.6;}
.box-container.active{ color:#f1323e; }
.box-container h2{ margin-bottom: 12px;}  
</style>