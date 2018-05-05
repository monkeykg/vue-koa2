<template>
  <div>
      <swiper :options="swiperOption">
          <swiper-slide class="swiper-slide" v-for='(item,index) in  recommendGoods' :key='index'>
              <img :src="item.image" alt="" width='80%'>
              <div>{{item.goodsName}}</div>
              <div>￥{{item.price}} (￥{{item.mallPrice}})</div>
          </swiper-slide>
          <div class='swiper-pagination' slot='pagination'></div>
      </swiper>
  </div>
</template>
<script>
import VueAwesomeSwiper from 'vue-awesome-swiper'
import 'swiper/dist/css/swiper.css'
export default {
  props:{
      recommendGoods:{
          type:Array,
      }
  },
  name:'swiperDefault',
  data(){
      return{
        //   slide:[1,2,3,4,5,6],
          swiperOption:{
                pagination:{
              el:'.swiper-pagination'
            },
                direction:'horizontal'
          }
      }
  }
}
</script>
<style lang="stylus">
    .swiper-slide
        height 4rem
        text-align center 
        border-bottom 1px solid #ccc
        
</style>

