<script setup>
import axios from "axios";
import { ref } from "vue";
const user = ref([]);
const url = ref("http://api.tvmaze.com/search/shows?q=golden%20girls");

function LoadData() {
  axios
    .get(url.value)
    .then((response) => {
      user.value = response.data;
    })
    .catch((err) => {
      console.log(err);
    });
}

</script>

<template>
  <h1>RandomUser</h1>
  <button style="width: 70px;" @click="LoadData()">Load</button>
  <table>
    <thead>
      <th>ลำดับที่</th>
      <th>Score</th>
      <th>Id</th>
      <th>Name</th>
      <th>Type</th>
      <th>Language</th>
      <th>Genres</th>
      <th>status</th>
      <th>runtime</th>
      <th>averageRuntime</th>
      <th>premiered</th>
      <th>ended</th>
    </thead>
    <tbody>
      <tr v-for="(value, index) in user" :key="index">
        <td>{{ index+1 }}</td>
        <td>{{ value.score }}</td>
        <td>{{ value.show.id }}</td>
        <td>{{ value.show.name }}</td>
        <td>{{ value.show.type }}</td>
        <td>{{ value.show.language }}</td>
        <td>{{ value.show.genres }}</td>
        <td>{{ value.show.status }}</td>
        <td>{{ value.show.runtime }}</td>
        <td>{{ value.show.averageRuntime }}</td>
        <td>{{ value.show.premiered }}</td>
        <td>{{ value.show.ended }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
  table,th,td,tr{
    border : 2px solid;
    color: greenyellow;
    text-align: center;
  }
  button{
    float : right;
  }
  h1{
    color: hsla(160, 100%, 37%, 1);
  }
</style>