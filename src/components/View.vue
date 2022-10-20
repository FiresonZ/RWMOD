<template>
    <div class="pure-u-1-5"><div class="l-box"><img class="pure-img" :src="Data.Img" style="width:64px;height:64px;"></div></div>
    <div class="pure-u-1-5"><div class="l-box"><p>{{Data.Name}}</p></div></div>
    <div class="pure-u-1-5"><div class="l-box"><p>{{Data.Author}}</p></div></div>
    <div class="pure-u-1-5"><div class="l-box"><p>{{Data.Version}}</p></div></div>
    <div class="pure-u-1-5"><div class="l-box"><a :href="Data.Adress">点击下载</a></div></div>
</template>

<script>
export default{
    props:{
        DataNum: Number
    },
    data(){
        return{
            Data:JSON.parse(localStorage.getItem('ModData'))[this.DataNum-1]
        }
    }
}
</script>