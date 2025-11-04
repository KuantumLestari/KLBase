<template>
  <AdminLayout>
    <div class="container-fluid py-3">
      <h4 class="fw-bold mb-1">Personnel Management</h4>
      <small class="text-muted">KLBase</small>

      <!-- Tabs -->
      <ul class="nav nav-tabs mt-4">
        <li class="nav-item" v-for="tab in tabs" :key="tab.name">
          <button
            class="nav-link"
            :class="{ active: currentTab === tab.name }"
            @click="currentTab = tab.name"
          >
            <i :class="tab.icon" class="me-2"></i>{{ tab.label }}
          </button>
        </li>
      </ul>

      <div class="tab-content mt-4">
        <div v-if="currentTab === 'contractors'">🚧 Contractors Page (To be developed)</div>
        <div v-if="currentTab === 'staff'">🚧 Staff Members Page (To be developed)</div>
        <div v-if="currentTab === 'visitors'">🚧 Visitors/Riders Page (To be developed)</div>
      </div>
    </div>
  </AdminLayout>
</template>

<script setup lang="ts">
import { ref } from "vue";
import AdminLayout from "../../layouts/AdminLayout.vue";

const tabs = [
  { name: "contractors", label: "Contractors", icon: "bi bi-person-badge" },
  { name: "staff", label: "Staff Members", icon: "bi bi-person-lines-fill" },
  { name: "visitors", label: "Visitors/Riders", icon: "bi bi-people" },
];

const currentTab = ref("contractors");
</script>
