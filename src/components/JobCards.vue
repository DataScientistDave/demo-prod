<script setup>
const { job } = defineProps(["job"]);
</script>

<template>
  <div class="card">
    <img :src="job.companyLogo" />
    <div>
      <h2>{{ job.companyName }}</h2>
      <h4>{{ job.title }}</h4>
      <p>Date Posted: {{ job.date }}</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 250px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
  border: 1px solid black;
  padding: 5px;
}
.card img {
  width: 100%;
}
</style>