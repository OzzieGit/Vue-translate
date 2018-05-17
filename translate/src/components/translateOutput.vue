<template>
  <div id="translateOutput">
  	<h2>{{ translatedText }}</h2>
  </div>
</template>
<script>
  export default {
    name: 'translateOutput',
    props:[
    	'translatedText'
    ]
  }
</script>
<style>
	#translateOutput{ font-size: 20px; color: #409EFF; font-weight: bold; margin-top: 40px; }
</style>
