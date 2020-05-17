<!-- FILE: readJSON.vue
We load the JSON from our backend via jqueries getJSON, this is then assigned to jsonData.
The template then loads the JSON in a couple of diffferent ways-->


<template>

  <div class="container-fluid">
    <div class="col-sm"></div>
    <div class="col-sm shadow-sm p-3 mb-5 bg-white rounded">
      <div class="alert alert-success alert-dismissible fade show" role="alert">
     Vue +  <strong>bootstrap</strong>
    <button type="button" class="close" data-dismiss="alert" aria-label="Close">
      <span aria-hidden="true">&times;</span>
    </button>
  </div>


    <p>JSON DATA: {{ jsonData }}</p>
    <p>JSON DATA: {{ jsonData.people[0]}}</p>
    <ul class="list-group">
      <li v-for="person in jsonData.people" :key="person.name" class="list-group-item">
     <b>Name:</b> {{ person.name }}, <b>Website:</b> {{ person.website }}, <b>From:</b> {{ person.from }}
      </li>
    </ul>
  </div>
  <div class="col-sm"></div>
  </div>
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
