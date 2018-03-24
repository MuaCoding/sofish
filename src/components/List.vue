<template>
    <div class="list">
      <template v-if="mold === 'thumbnail'" v-for="item in items">
        <router-link class="thumbnail">
          <div class="content">
            <img alt="cover">
            <h3>{{item.title}}</h3>
            <p>内容</p>
          </div>
          <div class="author">
            <span class="name">奖金</span>
            <span class="label">本活动来自</span>
          </div>
        </router-link>
      </template>
      <template v-if="mold === 'basic'">
        <ul class="basic" v-for="item in items">
          <li>
            <a href="#">
              <h3>33</h3>
              <div class="info">2222</div>
            </a>
          </li>
        </ul>
      </template>
    </div>
</template>

<script>
export default {
  name: 'list',
  props: {
    mold: {
      type: String,
      default: 'basic'
    },
    items:{
      type: Array,
      required: true
    }
  },
  data () {
    return {}
  },
  filters: {
    subStr: function(value){
      let newVal = value.replace(/<.*?>/g, '')
      return newVal.slice(0,30)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
  .list{
    .thumbnail{
      position: relative;
      display: block;
      padding: 2.5rem 1.8rem 2.5rem 0;
      margin-left: 1.8rem;
    }
  }
</style>
