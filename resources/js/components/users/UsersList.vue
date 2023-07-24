<script setup>
import { ref } from "vue";

let users = ref([]);

const getUsers = () => {
  axios
    .get("api/users")
    .then((res) => {
      console.log(res.data.data);
      users.value = res.data.data;
      console.log("users.value : ", users.value);
    })
    .catch((err) => console.log(err));
};

getUsers();
</script>

<template>
  <div>
    <div v-for="user in users" :key="user.id">
      <p>{{ user.name }}</p>
    </div>
  </div>
</template>

<style scoped>
</style>