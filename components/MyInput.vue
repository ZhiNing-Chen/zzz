<template>
    <div class=" m-3">
        
        <div class="form-group">
            <input type="text"
            class="form-control form-control-lg" aria-describedby="helpId" placeholder="输入你想新建的派系名" v-model="menu.pai">
        </div>
        <button type="button" class="btn btn-primary btn-lg btn-block" @click="add(menu)">新建派系</button>
    </div>
    
</template>

<script>
class Menu{
    constructor(pai,cai) {
          this.pai = pai;
          this.cai= cai;
        }
}
export default {
    data() {
        return {
            menu: new Menu('',[]),
        }
    },
    methods: {
        add:function(){
            this.$emit('my-pai',this.menu);
            this.menu=new Menu('',[]);
        }
    },
}
</script>