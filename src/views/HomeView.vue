<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>Made By Getters</h1>
  <div v-for='gettersUser in getUsers' :key='gettersUser.id'>
    {{gettersUser.id}} {{gettersUser.name}} {{gettersUser.address}}
    </div>
    <h1>Made By Actions</h1>
  <div v-for='user in users' :key='user.id'>
    {{user.id}} {{user.name}} {{user.address}}
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, computed } from 'vue';
//import users store
import { useUserStore } from "../store/index";
// declare store variable
const store = useUserStore();

const msg = ref("Welcome to my Vuex Store");

const getUsers = computed(() => {
  return store.getUsers
})
const users = computed(() => {
  return store.users
})

onMounted(() => {
  store.fetchUsers();
  store.checkLoggedInStatus();
})
</script>