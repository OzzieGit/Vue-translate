<template>
  <div id="translateForm">
    <!-- <div v-loading="true" ></div> -->
    <el-row :gutter="5">
      <el-col :span="6" :offset="9">
        <el-col :span="12"><el-input :span="2" type="text" placeholder="请输入搜索内容" v-model='textToTranslate'></el-input></el-col>
        <el-col :span="6">
          <el-select v-model="language">
            <el-option v-for="item in languageList" :label="item.label" :value="item.value">{{ item.label }}</el-option>
          </el-select>
        </el-col>
        <el-col :span="6"><el-button class='button' type="primary" @click="formSubmit">搜索</el-button></el-col>
      </el-col>
    </el-row>
  </div>
</template>
<script>
  export default {
    name: 'translateForm',
    data:function(){
      return {
        textToTranslate:"",
        languageList:[
          {
            value:'en',
            label:'English'
          },{
            value:'ru',
            label:'Russian'
          },{
            value:'ja',
            label:'Janpenese'
          },{
            value:'ko',
            label:'Korean'
          }
        ],
        language:"en"
      }
    },
    methods: {
      formSubmit:function(e){
        if(this.textToTranslate == ""){
          this.$alert('请输入搜索内容', '提示', {
            confirmButtonText: '确定',
            callback: action => { }
          });
        }else{
          this.$emit('formSubmit',this.textToTranslate, this.language);
        }
      }
    }
  }
</script>
<style>
.button{ display: block; width: 100% !important; }
</style>
