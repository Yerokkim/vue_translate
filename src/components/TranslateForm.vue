<template>
  <div id="TranslateForm">
    <h1>translator forline</h1>

    <form v-on:submit="formSubmit">

        <input type="text" v-model="textToTranslate" placeholder="word here">
         <select v-model="language">
      <option value="ru">Russian</option>
       <option value="ko">Korean</option>
        <option value="nl">Dutch</option>
      

    </select>
        <input type="submit" value="Submit">
    </form>
   
  </div>
</template>

<script>


export default {
  name: 'TranslateForm',
  data(){
      return{
          textToTranslate:'',
          language:''
      } 
  },
  created() {
      this.language='nl'
  },
  methods: {
      formSubmit(e){
          this.$emit('formSubmit',this.textToTranslate,this.language)
          e.preventDefault();
          
          

      }
  }
  
}
</script>

<style>
#TranslateForm {
  
}
</style>
