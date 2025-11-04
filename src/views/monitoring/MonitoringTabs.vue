<template>
  <AdminLayout>
    <div class="container-fluid py-3">
      <h4 class="fw-bold mb-1">Live Monitoring</h4>
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
        <div v-if="currentTab === 'gps'">🗺️ GPS Tracking Page (To be developed)</div>
        <div v-if="currentTab === 'cctv'">📹 CCTV Feeds Page (To be developed)</div>
        <div v-if="currentTab === 'zone'">📊 Zone Activity Page (To be developed)</div>
      </div>
    </div>
  </AdminLayout>
</template>

<script setup lang="ts">
import { ref } from "vue";
import AdminLayout from "../../layouts/AdminLayout.vue";

const tabs = [
  { name: "gps", label: "GPS Tracking", icon: "bi bi-geo" },
  { name: "cctv", label: "CCTV Feeds", icon: "bi bi-camera-video" },
  { name: "zone", label: "Zone Activity", icon: "bi bi-graph-up" },
];

const currentTab = ref("gps");
</script>
