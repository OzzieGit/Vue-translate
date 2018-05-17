<template>
  <div id="app" v-loading="loadStatic" element-loading-text="努力翻译中...">
    <div class="head">
      <h1>在线翻译</h1>
      <p>简单/易用/快捷</p>
    </div>
    <translateForm @formSubmit='translateText'></translateForm>
    <translateOutput v-text='translatedText'></translateOutput>
  </div>
</template>
<script>
  import TranslateForm from "./components/translateForm"
  import TranslateOutput from './components/translateOutput'
  export default {
    name: 'App',
    data:function(){
      return {
        translatedText:"",
        loadStatic:false
      }
    },
    components: {
      TranslateForm,
      TranslateOutput
    },
    methods:{
      translateText:function(text,language){
        this.translatedText = "";
        this.loadStatic = true;
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170721T082515Z.54cf3dc583f679db.f4a96182281281d8b5dfe24b4e88298e2133f219&lang='+ language +'&text='+text).then((response)=>{
          this.translatedText = response.data.text[0];
          this.loadStatic = false;
        }).catch((err)=>{
          console.log(err)
          this.loadStatic = false;
        })
      }
    }
  }
</script>
<style>
*{ margin: 0; padding: 0; list-style: none; }
body,html{ width: 100%; height: 100%; overflow: hidden; }
#app {
  font-family: "Helvetica Neue",Helvetica,"PingFang SC","Hiragino Sans GB","Microsoft YaHei","微软雅黑",Arial,sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 500px;
  position: fixed;top: 0; left: 0; bottom: 0; right: 0; margin: auto;
}
.head{ padding: 0 0 80px; }
.head h1{ font-size: 34px; margin-bottom: 20px; color: #409EFF; letter-spacing: 5px; }
.head p{ color: #999; font-size: 16px; letter-spacing: 5px; }
</style>
