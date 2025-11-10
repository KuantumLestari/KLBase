<template>
  <div>
      <div class="d-flex justify-content-between align-items-center mb-3">
      <h5 class="fw-semibold">CCTV Feeds</h5>
    </div>

    <!-- Stat Cards -->
 <div class="row mb-4 g-3">
      <div
        class="col-md-3"
        v-for="card in statCards"
        :key="card.label"
      >
        <div class="card shadow-sm border-0">
          <div class="card-body d-flex justify-content-between align-items-center">
            <div>
              <h4
                class="fw-bold mb-0"
                :class="{
                  'text-success': card.label === 'Active',
                  'text-danger': card.label === 'Alert'
                }"
              >
                {{ card.value }}
              </h4>
              <small class="text-muted">{{ card.label }}</small>
            </div>
            <i :class="card.icon" class="fs-3"></i>
          </div>
        </div>
      </div>
    </div>

    <!-- Live Feeds Grid -->
     <div class="row g-3">
      <div class="col-md-3" v-for="feed in liveFeeds" :key="feed.id">
        <div class="card bg-dark text-white border-0 shadow-sm video-card position-relative">
          <div class="video-placeholder d-flex align-items-center justify-content-center">
            <i class="bi bi-camera-video fs-1 text-secondary"></i>
          </div>

           <!-- LIVE label (top-left) -->
          <div class="position-absolute top-0 start-0 p-2 d-flex align-items-center">
            <span class="live-dot me-1"></span>
            <span class="fw-semibold small">LIVE</span>
          </div>

          <!-- ALERT badge (top-right, only if status is Alert) -->
          <div
            v-if="feed.status === 'Alert'"
            class="position-absolute top-0 end-0 bg-danger text-white px-2 py-1 fw-semibold small rounded-start"
          >
            Alert
          </div>

            <div class="card-footer bg-white text-dark">
              <h6 class="mb-0 fw-bold">{{ feed.name }}</h6>
              <small class="text-muted">{{ feed.zone }}</small>
            </div>
          </div>
        </div>
      </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const statCards = [
  { label: "Total Camera", value: 24, icon: "bi bi-camera-video text-primary" },
  { label: "Active", value: 18, icon: "bi bi-activity text-success" },
  { label: "Alert", value: 6, icon: "bi bi-exclamation-triangle text-danger" },
  { label: "Recording", value: 8, icon: "bi bi-record-circle text-info" },
];

// Mock data for video feeds
const liveFeeds = ref([
  { id: 1, name: 'Main Gate - Entrance', zone: 'Main Gate', status: 'Live' },
  { id: 2, name: 'Zone A - Building 1', zone: 'Zone A', status: 'Live' },
  { id: 3, name: 'Zone B - Warehouse', zone: 'Zone B', status: 'Alert' },
  { id: 4, name: 'Zone C - Parking', zone: 'Zone C', status: 'Live' },
  { id: 5, name: 'Zone D - Storage', zone: 'Zone D', status: 'Live' },
  { id: 6, name: 'Perimeter - North', zone: 'Perimeter', status: 'Live' },
  { id: 7, name: 'Perimeter - South', zone: 'Perimeter', status: 'Live' },
  { id: 8, name: 'Emergency Exit', zone: 'Exit', status: 'Live' },
]);
</script>

<style scoped>
/* Add custom styles if needed, e.g., for video placeholders */
.video-card {
  height: 200px; /* Adjust height as needed */
}

.video-placeholder {
  height: 100%;
  background-color: #212529; /* Dark background similar to the image */
}

/* Blinking green dot */
.live-dot {
  width: 8px;
  height: 8px;
  background-color: #28a745; /* Bootstrap green */
  border-radius: 50%;
  animation: blink 3s infinite;
}

@keyframes blink {
  0%, 50%, 100% {
    opacity: 1;
  }
  25%, 75% {
    opacity: 0.3;
  }
}

/* Make alert box stand out */
.bg-danger {
  background-color: #dc3545 !important;
}

.card-img-overlay {
  padding: 1rem;
}

.footer-info {
  background: linear-gradient(to top, rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0));
  margin: -1rem; /* Extend background to card edges */
  padding: 1rem;
}
</style>
