<template>
  <div id="app">
    <v-header></v-header>
    <div class='tab border-1px'>
      <div class='tab-item'>
        <router-link to='/goods'>商品</router-link>
      </div>
      <div class='tab-item'>
        <router-link to='/ratings'>评论</router-link>
      </div>
      <div class='tab-item'>
        <router-link to='/seller'>商家</router-link>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import axios from 'axios'
import header from './components/header/header.vue'
export default {
  name: 'app',
  data() {
    return {
      seller:{}
    }
  },
  components: {
    'v-header': header
  },
  methods:{
    get(){
      axios.get('./data.json')
      .then(function(res){
        console.log(res.data);
      }).catch(function(err){
         console.log(err);
      })
    }
  }
}
</script >

<style lang="stylus" rel="stylesheet/stylus">
  .tab
    display:flex
    width:100%
    height:40px
    line-height:40px
    .tab-item
      flex:1
      text-align:center
      & > a
        display: block
        text-decoration: none
        font-size: 14px
        color: rgb(77, 85, 93)
        &.router-link-active
          color: rgb(240, 20, 20)
</style>
