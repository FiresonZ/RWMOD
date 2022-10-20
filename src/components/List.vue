<template>
  <h1 style="position: absolute;top: 9%;left:4%;">模组列表</h1>
  <div style="position: absolute;top: 20%;left:4%;width:100%">
    <div class="pure-g" style="width:100%;">
      <div class="pure-u-1-5"><div class="l-box"><p></p></div></div>
      <div class="pure-u-1-5"><div class="l-box"><p>模组名称</p></div></div>
      <div class="pure-u-1-5"><div class="l-box"><p>作者</p></div></div>
      <div class="pure-u-1-5"><div class="l-box"><p>版本</p></div></div>
      <div class="pure-u-1-5"><div class="l-box"><p>下载</p></div></div>
    </div>
    <div class="pure-g" v-for="Pos in [1,2,3,4,5,6,7,8,9,10]" :style="{width:'100%',background:Pos%2?'GhostWhite':'White'}">
      <View v-if="Pos+PageCnt*10<=ModCnt" :DataNum=Pos+PageCnt*10></View>
    </div>
    <button class="pure-button pure-button-primary" @click="PageCnt>0?PageCnt--:null">上一页</button>
    <p>第{{PageCnt+1}}页</p>
    <button class="pure-button pure-button-primary" @click="PageCnt<ModCnt/10-1?PageCnt++:null">下一页</button>
  </div>
</template>

<script>
import View from './View.vue'
export default {
  components:{
    View
  },
  methods:{
    
  },
  data(){
    return{
      Data:JSON.parse(localStorage.getItem('ModData')),
      ModCnt:0,//Mod数量
      PageCnt:0//当前页数
    }
  },
  created:function(){
    this.ModCnt=this.Data.length;
  }
}
</script>

<style>

</style>
