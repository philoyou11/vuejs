<template>
  <li class="list-item">
    <h3>{{ item.username }}</h3>
    <p>{{ item.des }}</p>
  </li>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      required: true
    }
  },
  data () {
    return {}
  }
}
</script>

<style>
 
  .list-item{ padding: 10px;}

</style>