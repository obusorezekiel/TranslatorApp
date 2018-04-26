<template>
  <div id="translateForm">

      <form v-on:submit="formSubmit">
          <input type="text" v-model="textToTranslate" placeholder="Enter the text to be translated">
          <select v-model="language">
              <option value="ru">Russian</option>
              <option value="es">Spanish</option>
              <option value="fr">French</option>
              <option value="zh">Chinese</option>
              <option value="en">English</option>
              <option value="it">Italian</option>
              <option value="de">German</option>
              <option value="ja">Japanese</option>
              <option value="da">Danish</option>
              <option value="he">Hebrew</option>
              <option value="ko">Korean</option>
              <option value="sw">Swahili</option>
              <option value="cs">Czech</option>


          </select>  


          <input type="submit" value="Translate"/>


      </form>
    <TranslateForm></TranslateForm>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data(){
      return{
      textToTranslate:'',
      language:''
    } 
  },
  created(){
      this.language = 'ru';
  },
  methods:{
      formSubmit(e){
          //alert(this.textToTranslate);
          this.$emit('formSubmit', this.textToTranslate, this.language);
          e.preventDefault();
      }
  }


}
</script>
