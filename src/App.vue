<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->


    <Myheader :poiInfo='poiInfo'></Myheader>

    <Mynav></Mynav>


    <!-- 路由出口 -->
    <!-- 路由匹配到的组件将渲染在这里 -->
    <router-view></router-view>

  </div>
</template>

<script>

import Myheader from 'components/header/Header.vue'
import Mynav from 'components/Nav/Nav.vue'

export default {
  name: 'App',
  components: {
    Myheader,
    Mynav
  },
  data(){
    return{
      poiInfo: {}
    }
  },
  created(){   //ajax

    var that =this;

    this.$axios.get('/api/goods')
        .then(function (response) {
          var dataSource = response.data;
          if(dataSource.code == 0){
            that.poiInfo = dataSource.data.poi_info;
          }
        })
        .catch(function (error) {
          console.log(error);
        });
  }
}
</script>

<style>

</style>
