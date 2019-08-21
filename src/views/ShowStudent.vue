<template>
  <div class="show">
    <h1>{{ message }}</h1>
      <router-link v-bind:to="'localhost:8080/' + student.id">View this Student's PDF</router-link>
      <h2> Name: {{student.first_name + " " + student.last_name}}</h2>
      <p> Phone Number: {{student.phone_number}}</p>
      <p> Email: {{student.email}}</p>
      <p> Bio: {{student.bio}}</p>
      <p> Linkedin: {{student.linkedin}}</p>
      <p> Twitter: {{student.twitter}}</p>
      <p> Personal URL: {{student.personal_url}}</p>
      <p> Resume URL: {{student.resume_url}}</p>
      <p> GitHub: {{student.github_url}}</p>
      <h2> Capstone Name: {{capstone.name}}</h2>
      <p> Description: {{capstone.description}}</p>
      <p> URL: {{capstone.url}}</p>
      <p> Screenshot: {{capstone.screenshot}}</p>
      <h2> Experience: {{experience.job_title}}</h2>
      <p>Company: {{experience.company_name}}</p>
      <p>Start Date: {{experience.start_date}}</p>
      <p>End Date: {{experience.end_date}}</p>
      <p>Description: {{experience.details}}</p>
      <p>Education: {{education.university}}</p>
      <p>Degree: {{education.degree}}</p>
      <p>Start Date: {{education.start_date}}</p>
      <p>End Date: {{education.end_date}}</p>
      <p>Details: {{education.details}}</p>
      <h2>Skills: {{skill.name}}</h2>
   <!--    <p> GitHub: {{student.github_url}}</p>
      <p> GitHub: {{student.github_url}}</p>
      <p> GitHub: {{student.github_url}}</p> -->
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
      student: {},
      capstone: {},
      experience: {},
      education: {},
      skill: {}
    };
  },
  created: function() {
    axios.get('/api/students/' + this.$route.params.id).then(response => {
      console.log('in the show');
      this.student = response.data;
    });
    axios.get('/api/capstones/' + this.$route.params.id).then(response => {
      console.log('in the show');
      this.capstone = response.data;
    });
    axios.get('/api/experiences/' + this.$route.params.id).then(response => {
      console.log('in the show');
      this.experience = response.data;
    });
    axios.get('/api/educations/' + this.$route.params.id).then(response => {
      console.log('in the show');
      this.education = response.data;
    });
    axios.get('/api/skills/' + this.$route.params.id).then(response => {
      console.log('in the show');
      this.skill = response.data;
    });
  },
  methods: {}
};
</script>