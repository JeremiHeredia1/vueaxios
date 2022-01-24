<template>
  <div v-if="result" class="about">
    <h1>This is an about page Weather</h1>

    <p>Country: {{result.sys.country}}</p>
    <p>Location: {{ result.name }}<p>
    <img :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png'" alt="icono-clima"/> 
    <img :src="'http://openweathermap.org/img/w/'+result.weather[0].icon+'.png'" alt="icono-clima"/>
    <p>Timezone:{{result.timezone}}</p>
    <p>Temperature: {{ result.main.temp }}</p>
    <p>Weather: {{ result.weather[0].description }}</p>   
    <p>Maximum temperature: {{ result.main.temp_max }}</p>
    <p>Minimum temperature: {{ result.main.temp_min }}</p>
    <p>Humidity: {{ result.main.humidity }}</p>
    <p></p>
  </div>
  
  
</template>

<script>
import axios from "axios";
export default {
  data:()=>({
    result:null
  }),
    created() {
    let post = {
      title: "Example UTRM1",
      body: "<p>Example</p>",
      userId: 1,
    };
    let post_update = {
      title: "Example UTRM1",
      body: "<p>Example</p>",
      userId: 1,
    };

    axios.get("https://api.openweathermap.org/data/2.5/weather?q=Merida&appid=a173888a0ea468c6fe3f97ade32c46fe").then((result)=> {
      console.log(result.data);
      this.result=result.data;
      //console.log (result.data)
    }),
    axios.post("https://jsonplaceholder.typicode.com/posts", post).then((result) => {
      console.log(result);
    }),
    axios.put("https://jsonplaceholder.typicode.com/posts/1", post_update).then((result) => {
      console.log(result);
    });
  }
};

</script>
