<template>
  <div >
    <MyInput @my-pai="createPai"/>
    <MyCard :titles="cards" 
    @my-addcai="createCai"
    @my-sc="rm"
    @my-rmcard="rmcard"/>
  </div>
</template>

<script>

import MyInput from '@/components/MyInput'
import MyCard from '@/components/MyCard'

class Menu{
    constructor(pai,cai) {
          this.pai = pai;
          this.cai= cai;
        }
}

export default {
  name: 'App',
  components: {
    MyInput,
    MyCard
  },
  data() {
    return {
      cards:[
        new Menu('湘菜',['鱼香肉丝','辣椒炒肉']),
        new Menu('粤菜',['佛跳墙','白切鸭']),
        ],
    }
  },
  methods: {
    //新建派系
    createPai:function(menu){
      this.cards.push(menu);
    },
    //新建菜品
    createCai:function(i,cai){
      this.cards[i].cai.push(cai);
    },
    //删除菜品
      rm:function(i1,i2){
      this.cards[i1].cai.splice(i2,1);
    },
    //删除卡片
    rmcard:function(i){
      this.cards.splice(i,1)
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
