<template>
  <h1>Jobs</h1>
  <div v-for="job in jobs" :key="job" class="job">
    <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
      <h2>{{ job.title }}</h2>
    </router-link>
  </div>
</template>

<script>
export default {
  data() {
    return {
      jobs: [
        {
          id: 1,
          title: "Frontend Developer",
          description: "Figma or Adobe XD specialist",
        },
        {
          id: 2,
          title: "UI/UX Designer",
          description: "React JS and Vue JS developer",
        },
        {
          id: 3,
          title: "Backend Developer",
          description: "Node JS and Mongo DB developer",
        },
        {
          id: 4,
          title: "Data Analyst",
          description: "Python",
        },
      ],
    };
  },
};
</script>

<style>
.job h2{
    background: #f4f4f4;
    padding: 20px;
    border-radius: 10px;
    margin: 10px auto;
    max-width: 600px;
    cursor: pointer;
    color: #444;
    transition: all 0.3s ease-in-out;
}
.job h2:hover{
    background: #ddd;
}
.job a {
    text-decoration: none;
}
</style>
