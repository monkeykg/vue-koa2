<template>
  <div class="">
    <div class="search-bar">
      <van-row gutter='5'>
        <van-col span='3' class="search-icon"><i class="icon-address iconfont"></i></van-col>
        <van-col span='16'class='input'>
          <input type="text" class="search-input" placeholder="">
        </van-col>
        <van-col span='5' class="search-btn">
          <van-button size='small'>查找</van-button>
        </van-col>
      </van-row>
    </div>
    <div class="swiper-area">
      <van-swipe :autoplay='3000'>
        <van-swipe-item v-for="(image,index) in  bannerPicArray" :key='index'>
          <img :src='image.image' width="100%">
        </van-swipe-item>
      </van-swipe>
    </div>
    <div class="type-bar">
      <div v-for='(cate,index) in category' :key='index'>
        <img :src="cate.image" alt="" width="90%">
        <span>{{cate.mallCategoryName}}</span>
      </div>
    </div>
    <!-- ad banner area -->
    <div class='ad-banner'>
      <img :src="adBanner.PICTURE_ADDRESS" alt="">
    </div>
  </div>
</template>
<script>
import axios from 'axios'
export default {
  name:'ShoppingMall',
  data(){
      return{
         bannerPicArray:[
          //  {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic001.jpg'},
          //  {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic002.jpg'},
          //   {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic003.jpg'},
         ],
        category:[],
        adBanner:'',
      }
  },
  created(){
    axios({
      url:'https://easy-mock.com/mock/5ae7c0c7b1bff34114d6f4c5/mock/vue-loa2/smilevue',
      method:'get'
    }).then((Response)=>{
      console.dir(Response.data)
      if(Response.status==200){
        this.category=Response.data.data.category;
        this.adBanner=Response.data.data.advertesPicture;
        this. bannerPicArray=Response.data.data.slides;
      }
    }).catch((error)=>{
      console.log(error)
    })
  }
}
</script>
<style lang="stylus">
.search-bar
  height 2.2rem
  background #e5017d
  line-height 2.2rem
  .search-icon
    text-align center 
    .iconfont
      font-size 16px
      color #ffffff
  .input
    .search-input 
      width:100%;
      height: 1.3rem;
      border-top:0px;
      border-left:0px;
      border-right:0px;
      border-bottom: 1px solid #aeaeea !important ;
      background-color: #e5017d;
      color:#fff; 
      font-size 14px
      font-weight 700
      font-family: Arial, Helvetica, sans-serif
  .search-btn
    text-align center        
.swiper-area
  clear both
  width:20rem
  overflow hidden
.type-bar
  background #ffffff
  margin 0 .3rem .3rem .3rem
  border-radius 0.3rem
  font-size 14px
  display flex
  flex-direction row
  flex-wrap nowrap
  div
    padding .3rem
    font-size 12px
    text-align center
.ad-banner
  img 
    width 100%
</style>


