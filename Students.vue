<template>
  <div class="students">
    <h1>🌼 Students List: </h1>

    <!-- Static Students Using Props -->
    <StudentComponent
      v-for="student in students"
      :key="student.name"
      :name="student.name"
      :course="student.course"
      :year="student.year"
    />

    <h2>💛 API INTGRATION </h2>
    <p v-if="loading">Loading API data... 💛</p>
    <p v-if="error" class="error">{{ error }}</p>

    <ul v-if="users.length">
      <li v-for="user in users" :key="user.id">
        {{ user.name }} - {{ user.email }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
import StudentComponent from '../components/StudentComponent.vue'

export default {
  components: { StudentComponent },
  data() {
    return {
      students: [
        { name: "Anamarie Marquez", course: "BSIT", year: "4th Year" },
        { name: "Shaira Marquez", course: "BSED", year: "2nd Year" }
      ],
      users: [],
      loading: false,
      error: null
    }
  },
  mounted() {
    this.fetchUsers()
  },
  methods: {
    async fetchUsers() {
      this.loading = true
      try {
        const res = await axios.get('https://jsonplaceholder.typicode.com/users')
        this.users = res.data
      } catch (e) {
        this.error = "Failed to load API data"
      } finally {
        this.loading = false
      }
    }
  }
}
</script>

<style scoped>
.students {
  padding: 30px;
}

h1 {
  color: #6bcf2c; /* Girly Green */
}

h2 {
  margin-top: 30px;
  color: #f2c94c; /* Girly Yellow */
}

ul {
  background: #fff8c6;
  padding: 20px;
  border-radius: 15px;
  list-style: none;
}

li {
  padding: 8px;
  border-bottom: 1px solid #ddd;
}

.error {
  color: red;
  font-weight: bold;
}
</style>
