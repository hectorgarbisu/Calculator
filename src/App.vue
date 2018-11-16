<template>
  <div id="app" class="container">    
    <div class="card has-background-light">
      <header class="card-header">
        <h2 class="title is-2 is-medium has-text-info">Caluladora de swag</h2>
      </header>
    <the-swag-form @show-swag="showSwag($event)"/>
    <the-swag-score v-if="totalSwag>0" :score="totalSwag"/>
    </div>
  </div>
</template>


<script>

import TheSwagForm  from './the-swag-form.vue'
import TheSwagScore  from './the-swag-score.vue'

export default {

  name: "app",

  data() {
    return {
      totalSwag: 0,
    };
  },

  methods: {
    showSwag(totalSwag) {
      this.totalSwag = totalSwag
    },
  },

  components: { TheSwagForm, TheSwagScore},

};

</script>


<style>

  body {
    padding-top: 50px;
  }
  div.card {
    max-width: 720px;
  }
  header {
    padding-left: 20px;
    display: block;
  }

</style>
