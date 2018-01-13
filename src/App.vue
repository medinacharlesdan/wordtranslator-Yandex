<template>
  <div id="app" >
      <vue-particles
        color="#ff1234"
        :particleOpacity="0.7"
        :particlesNumber="50"
        shapeType="polygon"
        :particleSize="4"
        linesColor="#dedede"
        :linesWidth="1"
        :lineLinked="true"
        :lineOpacity="0.4"
        :linesDistance="150"
        :moveSpeed="3"
        :hoverEffect="true"
        hoverMode="grab"
        :clickEffect="true"
        clickMode="repulse"
        class="absolute"
      >
    </vue-particles>
    <div class="ui container">
 
   
    <h1 class="ui header ">
      
      <i class="hand lizard icon"></i>  
      <div class="content">
      Word translator
      </div>
    
      <a href="http://translate.yandex.com">
      <p class="sub header">
       Powered by Yandex.Translate
      </p>
      </a>

    </h1>

    <SearchForm v-on:outputLanguage="outputLanguage" v-on:textInput="theInputText"></SearchForm>
    
    <TranslatedOutput v-bind:language="language" v-bind:inputText="textTranslate"></TranslatedOutput>
      
    </div>
  </div>
</template>

<script>
import SearchForm from './components/SearchForm'
import TranslatedOutput from './components/TranslatedOutput'

export default {
  name: 'app',
  components:{
    SearchForm,
    TranslatedOutput
  },
  data(){
    return{
      language:"en",
      textTranslate:"",
      translated:""
    }
  },
  methods:{
    
    outputLanguage: function(lang){

      this.language = lang;
    },
    theInputText: function(textInput){
    
      this.textTranslate = textInput;
    
    }
    
    
   
  }
 
     
  
}
</script>

<style>
#app{
  padding: 2rem;
}

.absolute{
  position: absolute;
  width: 100%;
  height: 100%;
}
</style>
