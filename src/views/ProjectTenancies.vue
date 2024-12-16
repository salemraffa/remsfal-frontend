<script setup lang="ts">
import { ref, onMounted } from 'vue';

// Define props to get the projectId
defineProps<{
  projectId: string;
}>();

// Simulated data or API call
const projectData = ref<{ name: string; description: string } | null>(null);
const tenants = ref<{ name: string; address: string }[]>([]);

// Fetch project data based on projectId
const fetchProjectData = async () => {
  try {
    // Simulating an API call to fetch project details
    projectData.value = {
      name: `Project ${projectId}`,
      description: 'A description of the project.',
    };

    // Simulating tenant data
    tenants.value = [
      { name: 'John Doe', address: '123 Main St' },
      { name: 'Jane Smith', address: '456 Oak St' },
    ];
  } catch (error) {
    console.error('Error fetching project data:', error);
  }
};

// Call the fetchProjectData function on component mount
onMounted(() => {
  fetchProjectData();
});
</script>

<template>
  <main>
    <div class="grid">
      <!-- Project details section -->
      <h1>This is the project tenancy page for project {{ projectId }}.</h1>
      <div v-if="projectData">
        <h2>{{ projectData.name }}</h2>
        <p>{{ projectData.description }}</p>
      </div>

      <!-- Tenant list section -->
      <div class="tenant-list">
        <h3>Tenant Information</h3>
        <ul>
          <li v-for="(tenant, index) in tenants" :key="index">
            <p>{{ tenant.name }} - {{ tenant.address }}</p>
          </li>
        </ul>
      </div>

      <!-- Add tenant button (could open a form or modal to add a new tenant) -->
      <button @click="addTenant">Add Tenant</button>
    </div>
  </main>
</template>

<style scoped>
.grid {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tenant-list {
  margin-top: 20px;
  width: 100%;
  max-width: 600px;
}

button {
  margin-top: 20px;
  padding: 10px;
  background-color: #007BFF;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>

