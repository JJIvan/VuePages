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
      poiInfo: {
        "name": "深圳麦当劳明智餐厅",
        "shipping_time": "00:00-04:45,05:00-10:15,10:30-23:59",
        "wm_poi_score":4.7,
        "discounts2": [
          {
            "info": "新用户立减17元,首次使用银行卡支付最高再减3元",
            "icon_url": "http://p0.meituan.net/xianfu/019d1bbb1310b1531e6af6172c9a5095581.png"
          }
        ],
        "shipping_fee_tip": "配送 ¥9",
        "min_price_tip": "起送 ¥0",
        "delivery_time_tip": "30分钟",
        "poi_back_pic_url": "http://p1.meituan.net/aichequan/dfd39d77d47dfd6df4e1c07ab2e87458193641.png.webp",
        "pic_url": "http://p0.meituan.net/xianfu/fd3a8462080c71f60f2581c2e7c1d3f43010.jpeg.webp",
        "head_pic_url": "http://p0.meituan.net/xianfu/19c002c5963a289206e756092995a2fe230070.jpg"
      }
    }
  },
  created(){   //ajax

    /*var that =this;

    this.$axios.get('/api/goods')
        .then(function (response) {
          var dataSource = response.data;
          if(dataSource.code == 0){
            that.poiInfo = dataSource.data.poi_info;
          }
        })
        .catch(function (error) {
          console.log(error);
        });*/
  }
}
</script>

<style>

</style>
