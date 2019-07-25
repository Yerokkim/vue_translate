<template>
  <div id="app">
    <h1>how to order to Marc</h1>

    <TranslateForm @formSubmit="translateText"></TranslateForm>

    <TranslateOutput v-text="translatedText"></TranslateOutput>
    <button @click="pop">click</button>
  </div>
</template>

<script>

import TranslateForm from './components/TranslateForm'
import TranslateOutput from './components/TranslateOutput'

const api_key='trnsl.1.1.20190719T134213Z.173f82ca5ed13cf6.085f359a7e383196c719079493c73219abca6eaf'


export default {
  name: 'app',
  components: {
   TranslateForm,
   TranslateOutput

  },
  data:function(){
    return{
      translatedText:''
    }
  },
  
  methods: {
    translateText(text,language){
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=${api_key}&lang=${language}&text=${text}`)
      .then((res)=>{
        this.translatedText=res.body.text[0]
      })
    },

    pop(){
      alert('work')
    }
  },
}
</script>


