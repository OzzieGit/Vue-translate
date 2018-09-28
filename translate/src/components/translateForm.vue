<template>
  <div id="translateForm">
    <el-row :gutter="10">
      <el-col :sm="20" :md="6" :md-offset="9" style="margin: auto; float: none;">
        <el-col :sm="24" :md="12"><el-input :span="2" type="text" placeholder="请输入搜索内容" v-model='textToTranslate'></el-input></el-col>
        <el-col :sm="24" :md="6">
          <el-select class="select" v-model="language">
            <el-option v-for="item in languageList" :key="key" :label="item.label" :value="item.value">{{ item.label }}</el-option>
          </el-select>
        </el-col>
        <el-col :sm="24" :md="6"><el-button class='button' type="primary" @click="formSubmit">搜索</el-button></el-col>
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
        language:""
      }
    },
    methods: {
      formSubmit:function(){
        if(this.textToTranslate == ""){
          this.$alert('请输入搜索内容', '提示', {
            confirmButtonText: '确定',
            callback: action => { }
          });
        }else{
          this.$emit('formSubmit',this.textToTranslate, this.language);
        }
      }
    },
    created:function(){
      this.language = this.languageList[0].value
    }
  }
</script>
<style>
.button, .select{ display: block; width: 100% !important; }
@media screen and (max-width: 768px) {
  .el-col{ margin-bottom: 30px; padding: 0 30px !important; }
}
</style>
