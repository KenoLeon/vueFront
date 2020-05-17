<!-- FILE: readJSON.vue
We load the JSON from our backend via jqueries getJSON, this is then assigned to jsonData.
The template then loads the JSON in a couple of diffferent ways-->


<template>
  <span>
    <p>JSON DATA: {{ jsonData }}</p>
    <p>JSON DATA: {{ jsonData.people[0]}}</p>
    <ul>
      <li v-for="person in jsonData.people" :key="person.name">
     <b>Name:</b> {{ person.name }}, <b>Website:</b> {{ person.website }}, <b>From:</b> {{ person.from }}
      </li>
    </ul>
  </span>
</template>

<script>
import jQuery from 'jquery';
let $ = jQuery;

export default {
  created : function(){
    var _this = this;
    $.getJSON('https://py-back.rov.numerdash.com/data/', function (data) {
       _this.jsonData = data
    })
  },
  data: function() {
    return {
      jsonData: null
    };
  }
};
</script>

<style scoped>
span {
  font-size: 1.2em;
  text-align: center;
}
</style>
