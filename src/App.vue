<!--Tori Skinner-->
<!--CIS-131-->
<!--FINAL PROJECT-->
<!---->

<template>
  <div id="app">
    <HelloWorld v-bind:weatherList="weatherMain"></HelloWorld>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import axios from "axios";
export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      weatherMain:[],
      weatherImage:[],
      zip:'65802',
      units:'standard',
    };
  },
  methods:{
    changeAction(){
    if(this.zipFormat(this.zip) == true ){
      this.$emit('zip', this.zip);
      this.styleOfError = 'display: none';
    }else{
      this.styleOfError = 'display: inline-flex;  color: red';
    }
            
    },
        //Regex
    zipFormat(theValue){
      var validNum = /^\d{5}$|^\d{5}-\d{4}$/;
      return validNum.test(theValue);
    }
  },
  mounted() {
    axios.get(
      `https://api.openweathermap.org/data/2.5/weather?zip=${this.zip},us&units=${this.units}&appid=3dccb81dd046263c070cd0ea890e5f89`
    )
    .then((response) => {
      this.weatherMain = response.data;
  
    });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
