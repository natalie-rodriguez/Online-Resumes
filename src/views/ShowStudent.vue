<template>
  <div class="show">
    <h1>{{ message }}</h1>
      <h2> Name: {{student.first_name + " " + student.last_name}}</h2>
      <p> Phone Number: {{student.phone_number}}</p>
      <p> Email: {{student.email}}</p>
      <p> Bio: {{student.bio}}</p>
      <p> Linkedin: {{student.linkedin}}</p>
      <p> Twitter: {{student.twitter}}</p>
      <p> Personal URL: {{student.personal_url}}</p>
      <p> Resume URL: {{student.resume_url}}</p>
      <p> GitHub: {{student.github_url}}</p>
      <img v-bind:src="student.photo" v-bind:alt="student.first_name"/>
  </div>
</template>
<style>
</style>

<script>
import axios from 'axios';
export default {
  data: function() {
    return {
      message: "Welcome to Show!!",
      student: {}
    };
  },
  created: function() {
    axios.get('/api/students/' + this.$route.params.id).then(response => {
      console.log('in the show');
      this.student = response.data;
    });
  },
  methods: {}
};
</script>