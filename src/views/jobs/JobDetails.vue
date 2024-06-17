<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>{{ job.description }}</p>
  </div>
  <div v-else>Loading job details...</div>
  <div>{{ errorMsg }}</div>
</template>

<script>
export default {
  props: ["id"],
  // data(){
  //     return{
  //         id: this.$route.params.id
  //     }
  // },
  data() {
    return {
      job: null,
      errorMsg: "",
    };
  },
  mounted() {
    fetch("http://localhost:3000/jobs/" + this.id)
      .then((res) => {
        if (!res.ok) {
          throw new Error("This is a bad request");
        }
        return res.json();
      })
      .then((data) => {
        this.job = data;
        this.errorMsg = "";
      })
      .catch((error) => {
        this.errorMsg = "Error:" + error.message;
        this.job = null
      });
  },
};
</script>

<style></style>
