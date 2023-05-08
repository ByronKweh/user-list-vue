<template>
  <div class="content-container">
    <div class="content-header">
      <div class="header-overlay"></div>
      <div class="header-background"></div>
    </div>
    <div class="user-list">
      <h1>User List</h1>
      <button class="refresh-button" @click="fetchUsers">
        {{ hasLoaded ? 'Refresh List' : 'Load List' }}
      </button>
      <div v-if="loading">Loading...</div>
      <ul v-if="!loading" class="user-list-items">
        <li
          v-for="user in users"
          :key="user.login.uuid"
          class="user-list-item"
          @click="showDetails(user)"
        >
          {{ user.name.first }} {{ user.name.last }}
        </li>
      </ul>
      <user-details v-if="selectedUser" :user="selectedUser" @close="closeDetails" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'
import axios from 'axios'
import UserDetails from './UserDetails.vue'

interface User {
  login: {
    uuid: string
  }
  name: {
    first: string
    last: string
  }
}

export default defineComponent({
  name: 'UserList',
  components: {
    UserDetails
  },
  setup() {
    const users = ref<User[]>([])
    const selectedUser = ref<User | null>(null)
    const loading = ref(false)
    const hasLoaded = ref(false)

    async function fetchUsers() {
      loading.value = true
      const response = await axios.get('https://randomuser.me/api/?results=7')
      users.value = response.data.results
      loading.value = false
      hasLoaded.value = true
    }

    function showDetails(user: User) {
      selectedUser.value = user
    }

    function closeDetails() {
      selectedUser.value = null
    }

    return {
      users,
      selectedUser,
      loading,
      hasLoaded,
      fetchUsers,
      showDetails,
      closeDetails
    }
  }
})
</script>

<style scoped>
.content-container {
  display: flex;
  flex-direction: column;
}
.user-list {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.content-header {
  background-color: white;
  height: 100px;
  border: 1;
  width: 100%;
}
.header-background {
  background-color: white;
}
.refresh-button {
  background-color: #4caf50;
  border: none;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 16px;
  margin-bottom: 20px;
  cursor: pointer;
}

.user-list-items {
  list-style: none;
  padding: 0;
  margin: 0;
}

.user-list-item {
  padding: 10px;
  border: 1px solid #ccc;
  margin-bottom: 10px;
  cursor: pointer;
}

.user-list-item:hover {
  background-color: #f5f5f5;
  color: black;
}

.user-details {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.user-details h2 {
  margin-top: 0;
}
</style>
