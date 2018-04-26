<template>
  <div id="app">
    <h1>Translator Project in Vue.js</h1>
    <h5>Umesi Obusor</h5>
    <h6>Learnt from Traversy Media</h6>
    <TranslateForm v-on:formSubmit="translateText"></TranslateForm>
    <TranslateOutput v-text="translatedText"></TranslateOutput>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm';
import TranslateOutput from './components/TranslateOutput';


export default {
  name: 'app',
  components:{
    TranslateForm,
    TranslateOutput
  },

  data: function(){
    return {
    translatedText: ''
    }
  },

  methods:{
    translateText:function(text, language){
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20180425T200805Z.49fea1f2027b9e67.4021ded5293705b70f1fe39b41840093c9dda716&lang='+language+'&text='+text)
      .then((response) =>{
        this.translatedText = response.body.text[0];
      });
    }
  }

}
</script>
