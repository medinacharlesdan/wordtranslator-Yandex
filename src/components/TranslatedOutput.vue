<template>
  <div class="TranslatedOutput ui container">
   
    <div class="column">
    <div class="ui segment">
      <a class="ui blue ribbon label">Translation</a>
     
      <p>
        <h1 class="ui header center aligned">{{translated}}</h1>
      </p>

    </div>
     
    </div>
  </div>
</template>

<script>
export default {
    name:"TranslatedOutput",
    props: ['language', 'inputText'],
    data() {
      return{
        tLanguage : this.language,
        tInputText : this.inputText,
        translated : ""
      }
    },
    watch:{
        language: function(val){
   
        this.tLanguage = val;
        this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171230T165333Z.3d9468d8fb531987.79cfa14ee946b166f98c076a88358fe7f7767274&lang="+this.tLanguage+"&text="+ this.tInputText +"").then(response =>{
        this.translated = response.body.text[0];
             });
        
        },
        inputText:function(val){

        this.tInputText = val;

        this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171230T165333Z.3d9468d8fb531987.79cfa14ee946b166f98c076a88358fe7f7767274&lang="+this.tLanguage+"&text="+ this.tInputText +"").then(response =>{
        this.translated = response.body.text[0];
             });
        }
        
    },
    

}
</script>

<style>

</style>
