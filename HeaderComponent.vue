<template>
  <nav class="header">
    <h1 class="logo">🌼 Student Info App </h1>
    <div class="nav">
      <router-link to="/">Home</router-link>
      <router-link to="/students">Students</router-link>
    </div>
  </nav>
</template>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background: black;
  padding: 15px 30px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.3);
}

.logo {
  color: yellow;
  font-weight: bold;
}

.nav a {
  margin-left: 20px;
  text-decoration: none;
  color: #9cff57;
  font-weight: bold;
}

.nav a:hover {
  color: yellow;
}
</style>
