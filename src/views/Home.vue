<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="student in students">
      <h2> First Name: {{student.first_name}}</h2>
      <h2> Last Name: {{student.last_name}}</h2>
      <p> Email: {{student.email}}</p>
      <p> Phone Number: {{student.phone_number}}</p>
      <p> Bio: {{student.bio}}</p>
      <p> Linkedin: {{student.linkedin}}</p>
      <p> Twitter: {{student.twitter}}</p>
      <p> Personal URL: {{student.personal_url}}</p>
      <p> Resume URL: {{student.resume_url}}</p>
      <p> GitHub: {{student.github_url}}</p>
      <img v-bind:src="student.photo" v-bind:alt="student.first_name"/>
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