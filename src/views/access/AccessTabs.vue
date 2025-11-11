<template>
  <AdminLayout>
    <div class="container-fluid py-3">
      <h4 class="fw-bold mb-1">Access Control</h4>
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
       <component :is="currentTabComponent"></component>
        <div v-if="currentTab === 'qr'"> QR Management Page (To be developed)</div>
      </div>
    </div>
  </AdminLayout>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";
import AdminLayout from "../../layouts/AdminLayout.vue";
import AccessLogsView from "./AccessLogsView.vue";
import AccessRecordsView from "./AccessRecordsView.vue";

const tabs = [
  { name: "logs", label: "Access Logs", icon: "bi bi-journal-text" },
  { name: "records", label: "Entry/Exit Records", icon: "bi bi-box-arrow-in-right" },
  { name: "qr", label: "QR Management", icon: "bi bi-qr-code" },
];

const currentTab = ref("logs");
const currentTabComponent = computed(() => {
  const component: Record<string, any> = {
    logs:AccessLogsView,
    records: AccessRecordsView,
     qr: { template: "<div>🔐 QR Management Page (To be developed)</div>" },
  };
  return component[currentTab.value];
});
</script>
