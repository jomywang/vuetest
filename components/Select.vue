<template>
  
      <el-select v-on:change="changeSelect" v-model="value" placeholder="请选择" :name="name">
        <el-option
          v-for="item in options"
          :key="item"
          :label="item"
          :value="item">
        </el-option>
      </el-select>

</template>

<script>
  export default {
    data() {
      return {
        isData:false,
        options: [],
        value: ''

      }
    },
    props: ['dataName','name'],
    mounted:function(){
      this.getView();
    },
    methods:{
      getView(){
        var self = this;
        var time = setTimeout(function(){
          self.options = self.dataName;
          self.isData = true;         
        },100)       
      },
      changeSelect(){
         var valSelect = {};
         valSelect.name = this.name;
         valSelect.value = this.value;      
         this.$emit('selectVal',valSelect);
      }

    }
  }
</script>
<style>
</style>