<template>
  <div
    :class="[
      'd-flex flex-column bg-white border-end shadow-sm transition-all',
      collapsed ? 'sidebar-collapsed' : 'sidebar-expanded'
    ]"
  >
    <!-- Logo -->
    <div class="p-3 text-center border-bottom">
      <div v-if="!collapsed" class="fw-bold text-success fs-5">KLBase</div>
      <div v-else class="fw-bold text-success fs-4">K</div>
    </div>

    <!-- Nav -->
    <ul class="nav flex-column mt-3 text-nowrap">
      <li
        v-for="item in menu"
        :key="item.name"
        class="nav-item"
      >
        <a
          href="#"
          class="nav-link text-dark d-flex align-items-center px-3 py-2 reusable-hover"
          :class="{ active: active === item.name }"
          @click="setActive(item.name)"
        >
          <i :class="`bi ${item.icon} fs-5 me-2 text-success`"></i>
          <span v-if="!collapsed">{{ item.name }}</span>
        </a>
      </li>
    </ul>

    <!-- Spacer -->
    <div class="flex-grow-1"></div>

    <!-- Toggle Button -->
    <div class="text-center py-3 border-top">
      <button
        class="btn btn-sm btn-outline-success rounded-circle"
        @click="collapsed = !collapsed"
      >
        <i :class="collapsed ? 'bi bi-chevron-double-right' : 'bi bi-chevron-double-left'"></i>
      </button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const collapsed = ref(false);
const active = ref("Dashboard");

const setActive = (name: string) => {
  active.value = name;
};

const menu = [
  { name: "Dashboard", icon: "bi-house-door" },
  { name: "Personnel", icon: "bi-people" },
  { name: "Access", icon: "bi-geo-alt" },
  { name: "Security", icon: "bi-shield-lock" },
];
</script>

<style scoped>
.sidebar-expanded {
  width: 220px;
  transition: width 0.3s ease;
}

.sidebar-collapsed {
  width: 80px;
  transition: width 0.3s ease;
}

.nav-link {
  border-radius: 6px;
  transition: background-color 0.3s ease, color 0.3s ease;
}

.nav-link.active {
  background-color: rgba(25, 135, 84, 0.1);
  font-weight: 600;
}

.nav-link i {
  min-width: 20px;
  text-align: center;
}

.transition-all {
  transition: all 0.3s ease-in-out;
}
</style>
