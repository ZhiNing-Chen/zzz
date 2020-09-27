<template>
  <div class="row">
    <div class="col-3 mx-3" v-for="(item, index1) in titles" :key="index1">
      <div class="card">
        <div class="card-body">
          <h4 class="card-title">{{item.pai}}</h4>
          <hr />
          <div class="card mb-2" >
            <ul class="list-group list-group-flush">
              <li class="list-group-item" v-for="(item, index2) in item.cai" :key="index2" >{{item}}
                  <button type="button" class="btn btn-outline-danger float-right"  @click="sc(index1,index2)">X</button>
              </li>
            </ul>
          </div>
          <div class="form-group">
            <input type="text" class="form-control " v-model="cai" v-if="editIndex==index1"  placeholder >
          </div>
          <button type="button" name id class="btn btn-success btn-lg btn-block" v-if="editIndex==index1" @click="addCai(index1)">保存</button>
          <button type="button" name id class="btn btn-primary btn-lg btn-block" v-if="editIndex!=index1" @click="bian(index1)">新建菜名</button>
          <button type="button" name id class="btn btn-danger btn-lg btn-block" v-if="editIndex!=index1" @click="rmcard(index1)">删除卡片</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
      return {
          cai:'',
          editIndex: -1
      }
  },
  props: ["titles",],
  methods: {
      addCai:function(i){
          this.$emit('my-addcai',i,this.cai);
          this.cai='';
          this.editIndex=-1;
      },
      sc:function(i1,i2){
          this.$emit('my-sc',i1,i2);
      },
      bian:function(i){
        this.editIndex=i;
      },
      rmcard:function(i){
        this.$emit('my-rmcard',i);
      }
  },
};
</script>