<template>
<div>
  
  <div class="block">
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="currentPage4"
      :page-sizes="[2, 4, 6, 8]"
      :page-size="100"
      layout="total, sizes, prev, pager, next, jumper"
      :total="tbAll.length">
    </el-pagination>
  </div>
</div>
</template>
<script>
  import Bus from '../../static/js/controls/bus.js';  
  export default {
    data() {
      return {
        currentPage4: 1,
        tbAll:[],
        pagination:[]
      };
    },
    //props:['tableAllParent','tbAll'],
    created() {  
        Bus.$on('tableAllChild', (valAll) => {  
            this.tbAll =  valAll;
            console.log(valAll.length)
        });  
      },
    methods: {
      handleSizeChange(val) {
        //下拉改变
       var cur = `${val}`;
        Bus.$emit('curPage', cur);
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        var cur = `${val}`;
        Bus.$emit('curPage', cur);
      }
    }
    
  }
</script>
<style>
.el-pagination{text-align: right;}
</style>