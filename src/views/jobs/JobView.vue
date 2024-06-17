<template>
  <h1>Jobs</h1>
  <div v-if="jobs.length">
    <div v-for="job in jobs" :key="job" class="job">
      <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
        <h2>{{ job.title }}</h2>
      </router-link>
    </div>
  </div>
  <div v-else>Loading jobs...</div>
  <h4 v-if="errorMsg" class="error">{{ errorMsg }}</h4>
</template>

<script>
export default {
  data() {
    return {
      jobs: [],
      errorMsg: "",
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs")
      .then((res) => {
        if (!res.ok) {
          throw new Error("Network response was not ok");
        }
        return res.json();
      })
      .then((data) => (this.jobs = data))
      .catch((error) => {
        this.errorMsg = "Error fetching data: " + error.message;
      });
  },
};
</script>

<style>
.job h2 {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  margin: 10px auto;
  max-width: 600px;
  cursor: pointer;
  color: #444;
  transition: all 0.3s ease-in-out;
}
.job h2:hover {
  background: #ddd;
}
.job a {
  text-decoration: none;
}
.error {
  color: crimson;
  font-weight: bold;
}
</style>
