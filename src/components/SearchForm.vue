<template>
  <div class="SearchForm ui container">

    <div class="ui form">
    <div class="two fields">
    
    <div class="field">
    <label>Enter words you wanna translate</label>
    <input type="text" @keyup="textInput">
    <div class="ui pointing label">
        English phrase words only
    </div>
    </div>

    <div class="field">
    <label>Translate into:</label>
    <div class="ui dropdown search selection">
    <input type="hidden" name="Language" v-on:change="langChanged">
    <i class="dropdown icon"></i>
    <div class="default text">Select Language</div>
    <div class="menu">
        
        <div class="item" :data-value="code"  v-for="(lang,code) in languages">{{lang}}</div>
    
    </div>
    </div>
    </div>

    </div>
    </div>


  </div>
</template>

<script>

export default {
    name: "SearchForm",
    data()
    {
        return{
            languages:[],
            lang:"",
            code:""
        }
    },
    created: function() {
        this.$http.get("https://translate.yandex.net/api/v1.5/tr.json/getLangs?ui=en&key=trnsl.1.1.20171230T165333Z.3d9468d8fb531987.79cfa14ee946b166f98c076a88358fe7f7767274").then(resource =>{
            this.languages = resource.body.langs;
        });

      
    },
    mounted: function(){
         $('.ui.dropdown')
  .dropdown({
       transition: 'fade down'
  })
;
    },
    methods:{
        langChanged: function(e){
            console.log(e.target.value);
            this.$emit('outputLanguage', e.target.value, this.textToTranslate);
        },
        textInput:function(e){
          this.$emit('textInput', e.target.value);        }
    }
  
}
</script>

<style>

</style>
