<template>
  <div class="header">
    <div class="home-menu pure-menu pure-menu-horizontal pure-menu-fixed">
      <a class="pure-menu-heading" href="">RWMOD</a>
        <ul class="pure-menu-list">
          <li :class="Page=='Home'?'pure-menu-item pure-menu-selected':'pure-menu-item'"><a href="#" @click="Page='Home'" class="pure-menu-link">主页</a></li>
          <li :class="Page=='List'?'pure-menu-item pure-menu-selected':'pure-menu-item'"><a href="#" @click="Page='List'" class="pure-menu-link">模组</a></li>
          <li :class="Page=='About'?'pure-menu-item pure-menu-selected':'pure-menu-item'"><a href="#" @click="Page='About'" class="pure-menu-link">关于</a></li>
      </ul>
    </div>
  </div>
  <component :is="Page"></component>
  <div class="footer">
    <p>© 2022 - 铁锈战争模组浏览器</p>
  </div>
</template>

<script>
import axios from 'axios'
import List from './components/List.vue'
import Home from './components/Home.vue'
import About from './components/About.vue'
export default {
  components:{
    List,Home,About
  },
  data(){
    return{
      Page:'Home'
    }
  },
  mounted:function(){
    axios.get('/list.json')
    .then((res)=>{
      localStorage.setItem('ModData', JSON.stringify(res.data))
    })
    .catch((err)=>{
      console.log(err);
    })
    console.log('RWMOD加载成功!\n作者:FiresonZ\nhttps://github.com/FiresonZ\nhttps://firesonz.top');
  }
}
</script>

<style>
@import url(./assets/css/pure-min.css);
@import url(./assets/css/grids-responsive-min.css);
@import url(./assets/css/style.css)
</style>
