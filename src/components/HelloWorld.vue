<template>
  <div class="hello">
    <h1>City: {{ weatherList.name }}</h1>
    <p>Temperature: {{ weatherList.main.temp }}</p>
    <p>Current High: {{ weatherList.main.temp_max }}</p>
    <p>Current Low: {{ weatherList.main.temp_min }}</p>
    <p>Feels Like: {{ weatherList.main.feels_like }}</p>
    <input type="text" id="zipInput" />
    <button v-on:click="changeAction()">Submit</button> <!--fought with this for 4 hours i can't get it to work with the function.-->
    <!--text keeps repeating if I put it all into this div.im scared of deleting it, because i dont know what will happen, so it stays.-->
  </div>
</template> 

<script>
export default {
  name: "HelloWorld",
  props: ["weatherList"],
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

template{
  background-color: azure;
}

div {
  background-image: url("sky.jpg");
  background-repeat: no-repeat;
  background-size: cover;
}
</style>
