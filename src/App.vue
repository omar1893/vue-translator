<template>
  <div class="text-center" id="app">
   <h1>Word Translator</h1>
   <h5>Powered By Vue.js</h5>
   <translateForm v-on:formSubmit="translateText"></translateForm>
   <translateOutput v-text="translatedText"></translateOutput>

  </div>
</template>

<script>

import translateForm from './components/form'
import translateOutput from './components/output'

export default {
  name: 'app',
  components:{
    translateForm,
    translateOutput
  },
  data: function(){
    return {
      translatedText:''
    }
  },
  methods:{
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170415T224750Z.e6bc6abe34b650a9.35898e3d3c521ed19577d8f4396340ad47d11784&lang='+language+'&text='+text)
      .then((response) => {
        this.translatedText = response.body.text[0];
      })
    }
  }
}
</script>

<style>
#app {

}
</style>
