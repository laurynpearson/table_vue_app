<template>
  <div class="New Table">
    <h1>{{ message }}</h1>
    <div>
      <p>Name: <input type="text" v-model="newTableName"></p>
      <p>Height: <input type="text" v-model="newTableHeight"></p>
      <button v-on:click="createTable()">Make a New Table</button>
    </div>
  </div>
</template>
<style>
</style>

<script>
import axios from 'axios';
export default {
  data: function() {
    return {
      message: "Welcome to the New Table page!",
      newTableName: "",
      newTableHeight: ""
    };
  },
  created: function() {},
  methods: {
    createTable: function() {
      console.log("in create table");
      var newTable = {
        name: this.newTableName,
        height: this.newTableHeight
      };
      axios.post('/api/tables', newTable).then(response => {
        console.log('in the callback for create');
        console.log(response.data);
        this.$router.push('/');
      });
    }
  }
};
</script>
