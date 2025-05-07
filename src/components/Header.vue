<template>
  <header class="header">
    <div class="header-left">
      <button class="menu-toggle">
        <span></span>
        <span></span>
        <span></span>
      </button>
      <div class="search-container">
        <input type="text" placeholder="Search CodePen..." class="search-input" />
        <button class="search-btn">
          <svg viewBox="0 0 56.966 56.966" class="search-icon">
            <path d="M55.146,51.887L41.588,37.786c3.486-4.144,5.396-9.358,5.396-14.786c0-12.682-10.318-23-23-23s-23,10.318-23,23s10.318,23,23,23c4.761,0,9.298-1.436,13.177-4.162l13.661,14.208c0.571,0.593,1.339,0.92,2.162,0.92c0.779,0,1.518-0.297,2.079-0.837C56.255,54.982,56.293,53.08,55.146,51.887z M23.984,6c9.374,0,17,7.626,17,17s-7.626,17-17,17s-17-7.626-17-17S14.61,6,23.984,6z" />
          </svg>
        </button>
      </div>
    </div>
    <div class="header-right">
      <button class="create-btn" @click="createNewPen">Create</button>
      <div class="header-actions">
        <button class="action-btn">
          <svg viewBox="0 0 24 24" class="action-icon">
            <path d="M12 22c1.1 0 2-.9 2-2h-4c0 1.1.9 2 2 2zm6-6v-5c0-3.07-1.63-5.64-4.5-6.32V4c0-.83-.67-1.5-1.5-1.5s-1.5.67-1.5 1.5v.68C7.64 5.36 6 7.92 6 11v5l-2 2v1h16v-1l-2-2zm-2 1H8v-6c0-2.48 1.51-4.5 4-4.5s4 2.02 4 4.5v6z" />
          </svg>
        </button>
        <button class="action-btn">
          <svg viewBox="0 0 24 24" class="action-icon">
            <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm0 3c1.66 0 3 1.34 3 3s-1.34 3-3 3-3-1.34-3-3 1.34-3 3-3zm0 14.2c-2.5 0-4.71-1.28-6-3.22.03-1.99 4-3.08 6-3.08 1.99 0 5.97 1.09 6 3.08-1.29 1.94-3.5 3.22-6 3.22z" />
          </svg>
        </button>
      </div>
    </div>
  </header>
</template>

<script setup>
const emit = defineEmits(['createPen'])

function createNewPen() {
  emit('createPen')
}
</script>

<style scoped>
.header {
  height: 60px;
  background-color: #131417;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  border-bottom: 1px solid #2a2b31;
}

.header-left {
  display: flex;
  align-items: center;
  gap: 15px;
}

.menu-toggle {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  gap: 5px;
  padding: 5px;
}

.menu-toggle span {
  display: block;
  width: 20px;
  height: 2px;
  background-color: #fff;
}

.search-container {
  position: relative;
  display: flex;
  align-items: center;
}

.search-input {
  background-color: #1e1f26;
  border: 1px solid #2a2b31;
  border-radius: 4px;
  color: #fff;
  padding: 8px 35px 8px 12px;
  width: 200px;
  font-size: 14px;
}

.search-btn {
  position: absolute;
  right: 5px;
  background: none;
  border: none;
  cursor: pointer;
}

.search-icon {
  width: 16px;
  height: 16px;
  fill: #a7a9be;
}

.header-right {
  display: flex;
  align-items: center;
  gap: 15px;
}

.create-btn {
  background-color: #47cf73;
  color: #131417;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  font-weight: 600;
  cursor: pointer;
}

.header-actions {
  display: flex;
  gap: 10px;
}

.action-btn {
  background: none;
  border: none;
  cursor: pointer;
  padding: 5px;
}

.action-icon {
  width: 20px;
  height: 20px;
  fill: #a7a9be;
}
</style>