<script setup>

import { ref, computed } from 'vue'

import CreateUserForm from './components/CreateUserForm.vue'
import User from './components/User.vue'

// All Users
const users = ref([
  {
    id: 1,
    name: 'Daniel',
    age: 20,
    active: true
  },
  {
    id: 2,
    name: 'Hnin Hnin',
    age: 19,
    active: true
  },
  {
    id: 3,
    name: 'Kyaw Kyaw',
    age: 32,
    active: false
  }
])

// Active Users
const activeUsers = computed(_ => users.value.filter(user => user.active))

function createUser(name, age) {
  users.value.push({
    id: users.value.length + 1,
    name, age,
    active: true
  })
}

function updateUser(id, name, age) {
  console.log(id)
}

function deleteUser(id) {
  let user = users.value.find(user => user.id === id)
  user.active = false
}

</script>

<template>

  <!-- Heading -->
  <div>
    <h1>Active Users</h1>
  </div>

  <!-- Create -->
  <div>
    <create-user-form @create="createUser" />
  </div>

  <!-- Retrieve All -->
  <div>
    <span v-for="user in activeUsers">
      <user
        @update="updateUser"
        :key="user.id"
        :user="user"
      />
      <button @click="deleteUser(user.id)">🗑️</button>
    </span>
  </div>

</template>

<style scoped>

</style>
