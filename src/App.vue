<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="25%" />
    <ul>
      <li v-for="student in students" :key="student.id">
        {{ student.firstname }}
        {{ student.lastname }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      students: [],
    };
  },
  async mounted() {
    const result = await axios.get("http://localhost:8080/students");
    console.log(result);
    this.students = result.data;
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
