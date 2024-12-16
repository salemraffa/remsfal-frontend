<template>
  <div class="grid">
    <div class="task-list-wrapper">
      <div class="card">
        <h2>Tenancies</h2>
        <!-- Display TenancyMenu based on user role -->
        <TenancyMenu v-if="isAuthorizedUser" />
        <p v-else>You do not have permission to view this menu.</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import TenancyMenu from '@/components/layout/TenancyMenu.vue';
import { ref } from 'vue';

// Simulated user role check (you can replace this with actual logic)
const userRole = 'admin'; // Example role; replace with dynamic data
const isAuthorizedUser = ref(userRole === 'admin' || userRole === 'manager');
</script>

<style scoped>
.grid {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.task-list-wrapper {
  margin-top: 50px;
  width: 100%;
}

.card {
  padding: 20px;
  border-radius: 8px;
  display: flex;
  justify-content: center;
  width: 100%;
  max-width: 600px;
  margin: 20px 0;
}

.button-wrapper {
  display: flex;
  justify-content: center;
  width: 100%;
}

.button-wrapper button {
  width: 300px;
}
</style>
