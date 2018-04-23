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
  </div>
</template>
<script>
export default {
  name:'ShoppingMall',
  data(){
      return{
          msg:'Shopping Mall'
      }
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


</style>


