<script setup>
/* if want to include pinia*/
// import { useUsersStore } from "~/store/users";
// const UsersStore = useUsersStore();
// //console.log(UsersStore);
</script>
<template>
  <!-- <div class="text-center homepage">Welcome to nuxt3</div> -->
  <NuxtLink to="/users/create">Create User</NuxtLink>
  <NuxtLink to="/users/694/edit">Edit User</NuxtLink>
</template>
<style scoped>
.homepage {
  margin-top: 400px;
  font-size: 30px;
}
</style>
