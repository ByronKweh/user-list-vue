<template>
  <div>
    <h2>{{ user.name.first }} {{ user.name.last }}</h2>
    <p>{{ user.email }}</p>
    <p>{{ user.phone }}</p>
    <p>{{ user.location.city }}, {{ user.location.country }}</p>
    <button @click="$emit('close')">Close</button>
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
