<template>
  <div id="app">
    <backzj v-show="$route.meta.back"/>
    <keep-alive>
      <router-view v-if="isRouterAlive && $route.meta.keepAlive"></router-view>
    </keep-alive>
    <router-view v-if="isRouterAlive && !$route.meta.keepAlive"></router-view>
    <dibutarber v-show="$route.meta.tarber"/>
    <m-loading ref="comLoading" v-bind:alert="loadingAlert" v-bind:isShow="isShowLoading"></m-loading>
  </div>
</template>

<script>
import Backzj from './components/backzj.vue'
import Dibutarber from './components/dibutarber.vue'
export default {
  components: { Dibutarber, Backzj },
  name: 'App',
  provide(){
    return{
      reload:this.reload,
    }
  },
  data(){
    return{
      isRouterAlive:true,
      loadingAlert:"正在加载中...AAAAAAAAAAAAAAAAAAAAA...",
      isShowLoading:false,
    }
  },
  methods:{
    reload(){
        this.isRouterAlive=false
        this.$nextTick(function(){
            this.isRouterAlive=true
        })
    }
  }
}
</script>

<style>
*{padding: 0;margin: 0;}
html,body,#app{
  height: 100%;
  background: #f6f6f6;
  font-size: 15px;
  /* font-family: ; */
}
.zhezhao{
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background: rgba(68, 68, 68, 0.5);
  z-index: 100;
}
.padd{padding: 0 10px;}
.zhanwei{width: 100%;height: 100px;}
.dbuzw{width: 100%;height: 40px;}
.setPosCenter {
  margin: 0 auto;
}
</style>
