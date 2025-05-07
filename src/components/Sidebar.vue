<template>
  <div class="sidebar">
    <div class="logo-container">
      <div class="logo">
        <svg viewBox="0 0 100 100" class="codepen-logo">
          <path d="M100 34.2c-.4-2.6-3.3-4-5.3-5.3-3.6-2.4-7.1-4.7-10.7-7.1-8.5-5.7-17.1-11.4-25.6-17.1-2-1.3-4-2.7-6-4-1.4-1-3.3-1-4.8 0-5.7 3.8-11.5 7.7-17.2 11.5L5.2 29C3 30.4.1 31.8 0 34.8c-.1 3.3 0 6.7 0 10v16c0 2.9-.6 6.3 2.1 8.1 6.4 4.4 12.9 8.6 19.4 12.9 8 5.3 16 10.7 24 16 2.2 1.5 4.4 3.1 7.1 1.3 2.3-1.5 4.5-3 6.8-4.5 8.9-5.9 17.8-11.9 26.7-17.8l9.9-6.6c.6-.4 1.3-.8 1.9-1.3 1.4-1 2-2.4 2-4.1V37.3c.1-1.1.2-2.1.1-3.1 0-.1 0 .2 0 0zM54.3 12.3L88 34.8 73 44.9 54.3 32.4V12.3zm-8.6 0v20L27.1 44.8 12 34.8l33.7-22.5zM8.6 42.8L19.3 50 8.6 57.2V42.8zm37.1 44.9L12 65.2l15-10.1 18.6 12.5v20.1zM50 60.2L34.8 50 50 39.8 65.2 50 50 60.2zm4.3 27.5v-20l18.6-12.5 15 10.1-33.6 22.4zm37.1-30.5L80.7 50l10.8-7.2-.1 14.4z"></path>
        </svg>
        <span>CodePen</span>
      </div>
    </div>
    
    <nav class="sidebar-nav">
      <ul>
        <li class="nav-item active">
          <a href="#">
            <i class="icon">🏠</i>
            <span>Home</span>
          </a>
        </li>
        <li class="nav-item">
          <a href="#">
            <i class="icon">🔍</i>
            <span>Explore</span>
          </a>
        </li>
        <li class="nav-item">
          <a href="#">
            <i class="icon">✏️</i>
            <span>Create</span>
          </a>
        </li>
        <li class="nav-item">
          <a href="#">
            <i class="icon">👥</i>
            <span>Community</span>
          </a>
        </li>
        <li class="nav-item">
          <a href="#">
            <i class="icon">💼</i>
            <span>Jobs</span>
          </a>
        </li>
      </ul>
    </nav>
    
    <div class="sidebar-footer">
      <button class="sign-in-btn">Sign In</button>
      <button class="sign-up-btn">Sign Up</button>
    </div>
  </div>
</template>

<script setup>
// Sidebar component logic can go here
</script>

<style scoped>
.sidebar {
  width: 220px;
  height: 100vh;
  background-color: #1e1f26;
  color: #fff;
  display: flex;
  flex-direction: column;
  border-right: 1px solid #2a2b31;
}

.logo-container {
  padding: 20px;
  border-bottom: 1px solid #2a2b31;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.codepen-logo {
  width: 30px;
  height: 30px;
  fill: #fff;
}

.logo span {
  font-size: 18px;
  font-weight: bold;
}

.sidebar-nav {
  flex: 1;
  padding: 20px 0;
}

.sidebar-nav ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.nav-item {
  margin-bottom: 5px;
}

.nav-item a {
  display: flex;
  align-items: center;
  padding: 10px 20px;
  color: #a7a9be;
  text-decoration: none;
  transition: all 0.2s ease;
}

.nav-item a:hover {
  background-color: #2a2b31;
  color: #fff;
}

.nav-item.active a {
  background-color: #2a2b31;
  color: #fff;
  border-left: 3px solid #47cf73;
}

.icon {
  margin-right: 10px;
  font-size: 16px;
}

.sidebar-footer {
  padding: 20px;
  border-top: 1px solid #2a2b31;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.sign-in-btn, .sign-up-btn {
  padding: 8px;
  border-radius: 4px;
  border: none;
  cursor: pointer;
  font-weight: 500;
  width: 100%;
}

.sign-in-btn {
  background-color: transparent;
  border: 1px solid #47cf73;
  color: #47cf73;
}

.sign-up-btn {
  background-color: #47cf73;
  color: #1e1f26;
}
</style>