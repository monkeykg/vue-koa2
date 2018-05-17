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
    <!-- 商品推荐区域 -->
    <div class="recommend-area">
      <div class="recommend-title">商品推荐</div>
      <div class="recommend-body">
        <!-- <swiper >
          <swiper-slide v-for="(item,index) in recommendGoods" :key='index'>
            <div class="recommend-item">
              <img :src="item.image" alt="" width='80%'>
              <div>{{item.goodsName}}</div>
              <div>￥{{item.price}} (￥{{item.mallPrice}})</div>
            </div>
          </swiper-slide>
        </swiper> -->
        <swiperDefault :recommendGoods='recommendGoods'></swiperDefault>
      </div> 
    </div>
    <!-- 楼层 区域 -->
    <floorComponent :floorData='floor1' :floorTitle='floorName.floor1'></floorComponent>
    <floorComponent :floorData='floor2' :floorTitle='floorName.floor2'></floorComponent>
    <floorComponent :floorData='floor3' :floorTitle='floorName.floor3'></floorComponent>
    <!-- 热门商品区域 hot area -->
    <div class="hot-area"> 
      <div class='hot-title'>热卖商品</div>
      <div class="hot-goods"> 
        <!-- list -->
        <van-list>
          <van-row gutter='20'>
            <van-col span='12' v-for='(item,index) in hotGoods' :key='index' >
              <goodsInfo :goodsImage='item.image' :goodsName='item.name' :goodsPrice="item.price"></goodsInfo>
            </van-col>
          </van-row>
        </van-list>
      </div> 
    </div> 

  </div>
</template>
<script>
import axios from 'axios'
import swiperDefault from '@/components/swiper/swiperDefault.vue'
import floorComponent from '@/components/pages/floorComponent.vue'
import goodsInfo from '@/components/pages/goodsInfo.vue'
export default {
  name:'ShoppingMall',
  components:{
  swiperDefault,
  floorComponent,
  goodsInfo
  },
  data(){
      return{
         bannerPicArray:[
          //  {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic001.jpg'},
          //  {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic002.jpg'},
          //   {imageUrl:'http://7xjyw1.com1.z0.glb.clouddn.com/simleVueDemoPic003.jpg'},
         ],
        category:[],
        adBanner:'',
        recommendGoods:[],
        // floor1_0:{},
        // floor1_1:{},
        // floor1_2:{},
        floor1:[],
        floor2:[],
        floor3:[],
        floorName:{},
        hotGoods:[],
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
        this.bannerPicArray=Response.data.data.slides;
        this.recommendGoods=Response.data.data.recommend;
        this.floor1=Response.data.data.floor1;
        this.floor2=Response.data.data.floor2;
        this.floor3=Response.data.data.floor3;
        this.floorName=Response.data.data.floorName;
        this.hotGoods=Response.data.data.hotGoods;

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
      height: 1.5rem;
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
.recommend-area
  background-color #fff
  margin-top .3rem   
  .recommend-title
    border-bottom 1px solid #eeeeee
    font-size 14px
    padding 0.2rem
    color #e5017d
  .recommend-body
    .recommend-item
      width 100%
      border-right 1px solid #eeeeee
      font-size 12px 
      font-weight 700
      text-align center
.hot-area
  text-align center
  font-size 14px
  height 1.8rem
  line-height 1.8rem      
</style>


