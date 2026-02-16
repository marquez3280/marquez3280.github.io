<template>
  <div class="card">
    <h2>{{ name }}</h2>
    <p><strong>Course:</strong> {{ course }}</p>
    <p><strong>Year:</strong> {{ year }}</p>

    <!-- Status shows when button clicked -->
    <p v-if="showStatus">
      <strong>Status:</strong>
      <span :class="statusClass">{{ currentStatus }}</span>
    </p>

    <button @click="toggleStatus">
      {{ showStatus ? "Hide Status" : "View Info" }}
    </button>
  </div>
</template>

<script>
export default {
  props: {
    name: String,
    course: String,
    year: String,
    status: {
      type: String,
      default: 'Active' 
    }
  },
  data() {
    return {
      showStatus: false,
      currentStatus: this.status // use reactive variable
    }
  },
  computed: {
    statusClass() {
      return this.currentStatus === 'Active' ? 'active' : 'inactive';
    }
  },
  methods: {
    toggleStatus() {
      this.showStatus = !this.showStatus;
    }
  }
}
</script>

<style scoped>
.card {
  background: white;
  border-left: 8px solid #9cff57;
  padding: 20px;
  margin: 15px;
  border-radius: 15px;
  box-shadow: 0 6px 12px rgba(0,0,0,0.1);
  transition: 0.3s;
}

.card:hover {
  transform: scale(1.03);
}

button {
  background: yellow;
  border: none;
  padding: 10px 15px;
  border-radius: 20px;
  font-weight: bold;
  cursor: pointer;
  margin-top: 10px;
}

button:hover {
  background: #9cff57;
}

.active {
  color: green;
  font-weight: bold;
}

.inactive {
  color: red;
  font-weight: bold;
}
</style>
