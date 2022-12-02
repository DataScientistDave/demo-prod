<script setup>
import { ref, watch } from "vue";
import jobsData from "../data/jobs.json";
import JobCards from "./components/JobCards.vue";
const showSearch = ref(false);
const search = ref("");
const jobs = ref(jobsData);

const toggleSearch = () => {
  showSearch.value = !showSearch.value;
};

watch(search, () => {
  jobs.value = jobsData.filter((job) =>
    job.title.toLowerCase().includes(search.value.toLowerCase())
  );
});
</script>

<template>
  <main>
    <div class="container">
      <header>
        <h1>Jobs Board</h1>
        <input
          v-if="showSearch"
          v-model="search"
          type="text"
          placeholder="search"
        />
      </header>
      <button @click="toggleSearch">Toggle Search</button>
    </div>
    <div class="card-container">
      <JobCards v-for="job in jobs" :key="job.id" :job="job" />
    </div>
  </main>
</template>



<style scoped>
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 0 2rem;
}
main {
  height: 100vh;
  width: 100vw;
}
.card-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 5rem;
}
</style>