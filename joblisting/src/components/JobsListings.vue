<script setup>
  import Joblisting from './Joblisting.vue';
  import jobData from '../assets/jobs.json';
  import { ref } from 'vue';

const jobs  = ref (jobData);

</script>

<template>
    <!-- Browse Jobs -->
    <section class="bg-green-50 px-4 py-10">
      <div class="container-xl lg:container m-auto">
        <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
          Browse Jobs
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <Joblisting v-for="job in jobs":key="jobs.id" :job="job"/>
         </div>
      </div>   
         
    </section>
</template>