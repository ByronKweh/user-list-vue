<template>
  <div class="user-details-overlay">
    <div class="user-details-content">
      <div class="user-details-header">
        <h2>{{ user.name.first }} {{ user.name.last }}</h2>
      </div>
      <div class="user-details-info">
        <div class="user-details-picture">
          <img :src="user.picture.large" alt="User Picture" />
        </div>
        <div class="user-details-text">
          <ul>
            <li><i class="fas fa-at"></i> Email: {{ user.email }}</li>
            <li><i class="fas fa-phone"></i> Phone number: {{ user.phone }}</li>
            <li>
              <i class="fas fa-map-marker-alt"></i>
              Addres: {{ user.location.street.number }} {{ user.location.street.name }},
              {{ user.location.city }}, {{ user.location.state }}, {{ user.location.country }},
              {{ user.location.postcode }}
            </li>
            <li><i class="fas fa-venus-mars"></i>Gender: {{ user.gender }}</li>
            <li><i class="fas fa-user"></i> Username: {{ user.login.username }}</li>
            <li><i class="fas fa-lock"></i> Password: {{ user.login.password }}</li>
            <li>
              <i class="fas fa-calendar-alt"></i> Registered on
              {{ new Date(user.registered.date).toLocaleDateString() }}
            </li>
            <li><i class="fas fa-id-card"></i> {{ user.id.name }}: {{ user.id.value }}</li>
            <li><i class="fas fa-globe"></i> Nationality: {{ user.nat }}</li>
          </ul>
        </div>
        <button class="close-button" @click="$emit('close')">X</button>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, type PropType } from 'vue'

export default defineComponent({
  name: 'UserDetails',
  props: {
    user: {
      type: Object as PropType<any>,
      required: true
    }
  }
})
</script>

<style scoped>
.user-details-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.user-details-content {
  background-color: white;
  padding: 20px;
  max-width: 600px;
  width: 100%;
  color: black;
  border-radius: 10px;
}

.user-details-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.user-details-header h2 {
  margin: 0;
}

.close-button {
  position: absolute;
  top: -50px;
  right: 10px;
  background-color: transparent;
  border: none;
  font-size: 1.5rem;
  color: #999;
  cursor: pointer;
  transition: color 0.3s ease-in-out;
}

.close-button:hover {
  color: black;
}

.user-details-info {
  display: flex;
}

.user-details-picture {
  width: 200px;
  margin-right: 20px;
}

.user-details-picture img {
  max-width: 100%;
  border-radius: 10px;
}

.user-details-text ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.user-details-text ul li {
  margin-bottom: 10px;
}
</style>
