<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="student in students">
      <h2> Name: {{student.first_name + " " + student.last_name}}</h2>
      <p><router-link v-bind:to="'/students/' + student.id">View this Student's Resume</router-link></p>
      <hr>
    </div>
    
  </div>
</template>

<style>
</style>

<script>


import axios from 'axios';
export default {
  data: function() {
    return {
      message: "Welcome to the index!",
      students: []
    };
  },
  created: function() {
    axios.get('/api/students').then(response => {
      console.log('in the index');
      this.students = response.data;
    });
  },
  methods: {}
};
</script>
