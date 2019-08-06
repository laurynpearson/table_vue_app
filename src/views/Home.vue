<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="table in tables">
      <h2> {{ table.name }}</h2>
        <p>{{table.height}}</p>
      <hr>
    </div>
      
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "All Tables!",
      tables: []
    };
  },
  created: function() {
    axios.get("/api/tables").then(response => {
      this.tables = response.data
    });
  },
  methods: {}
};
</script>
