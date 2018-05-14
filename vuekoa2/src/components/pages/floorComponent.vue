<template>
  <div class="floors">
      <div class="floor">
          <div class="floor-tittle">{{floorTitle}}</div>
          <div class="floor-swipper">
              <div class="floor-one">
                  <img :src="floorData0.image" alt="" width="100%">
              </div>
              <div>
                  <div class="floor-two"><img :src="floorData1.image" alt="" width="100%"></div>
                  <div><img :src="floorData2.image" alt="" width="100%"></div>
              </div>
          </div>
          <div class="floor-rule">
              <div v-for="(item,index) in floorData.slice(3)" :key="index">
                  <img :src="item.image" alt="" width='100%'>
              </div>
          </div>
      </div>
  </div>
</template>
<script>
export default {
  name:'floorComponent',
  props:{
       floorData:{
           type:Array
       },
       floorTitle:{
           type:String
       }
  },
  data(){
      return{
          floorData0:{},
          floorData1:{},
          floorData2:{},
      }
  },
  create(){

  },
  watch:{
      floorData:function(val){
        //   console.log(this.floorData)
          this.floorData0=this.floorData[0]
          this.floorData1=this.floorData[1]
          this.floorData2=this.floorData[2]
      }
  }
}
</script>
<style lang="stylus">
    .floor-tittle
        text-align center 
        font-size 14px
        height 1.8rem
        line-height 1.8rem
    .floor-swipper
        display flex
        flex-direction row
        background #ffffff
        border-bottom 1px solid #dddddd
        div
            width 10rem
    .floor-rule
        display flex
        flex-direction row
        flex-wrap wrap 
        background #fff 
        div
            width 10rem
</style>

