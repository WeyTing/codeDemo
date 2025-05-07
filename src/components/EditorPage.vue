<template>
  <div class="editor-page">
    <div class="editor-header">
      <div class="header-left">
        <div class="logo" @click="goToHome">
          <svg viewBox="0 0 100 100" class="codepen-logo">
            <path d="M100 34.2c-.4-2.6-3.3-4-5.3-5.3-3.6-2.4-7.1-4.7-10.7-7.1-8.5-5.7-17.1-11.4-25.6-17.1-2-1.3-4-2.7-6-4-1.4-1-3.3-1-4.8 0-5.7 3.8-11.5 7.7-17.2 11.5L5.2 29C3 30.4.1 31.8 0 34.8c-.1 3.3 0 6.7 0 10v16c0 2.9-.6 6.3 2.1 8.1 6.4 4.4 12.9 8.6 19.4 12.9 8 5.3 16 10.7 24 16 2.2 1.5 4.4 3.1 7.1 1.3 2.3-1.5 4.5-3 6.8-4.5 8.9-5.9 17.8-11.9 26.7-17.8l9.9-6.6c.6-.4 1.3-.8 1.9-1.3 1.4-1 2-2.4 2-4.1V37.3c.1-1.1.2-2.1.1-3.1 0-.1 0 .2 0 0zM54.3 12.3L88 34.8 73 44.9 54.3 32.4V12.3zm-8.6 0v20L27.1 44.8 12 34.8l33.7-22.5zM8.6 42.8L19.3 50 8.6 57.2V42.8zm37.1 44.9L12 65.2l15-10.1 18.6 12.5v20.1zM50 60.2L34.8 50 50 39.8 65.2 50 50 60.2zm4.3 27.5v-20l18.6-12.5 15 10.1-33.6 22.4zm37.1-30.5L80.7 50l10.8-7.2-.1 14.4z"></path>
          </svg>
          <span>CodePen</span>
        </div>
        <div class="pen-title">
          <input type="text" placeholder="Untitled Pen" class="title-input" />
        </div>
      </div>
      <div class="header-right">
        <button class="header-btn save-btn">Save</button>
        <button class="header-btn settings-btn">Settings</button>
        <div class="user-menu">
          <div class="user-avatar"></div>
          <span class="username">Username</span>
        </div>
      </div>
    </div>

    <div class="editor-toolbar">
      <div class="toolbar-left">
        <button class="toolbar-btn" @click="goToHome">
          <span class="btn-icon">🏠</span>
          <span class="btn-text">Home</span>
        </button>
        <button class="toolbar-btn">
          <span class="btn-icon">📁</span>
          <span class="btn-text">File</span>
        </button>
        <button class="toolbar-btn">
          <span class="btn-icon">⚙️</span>
          <span class="btn-text">Edit</span>
        </button>
        <button class="toolbar-btn">
          <span class="btn-icon">👁️</span>
          <span class="btn-text">View</span>
        </button>
        <button class="toolbar-btn">
          <span class="btn-icon">🔧</span>
          <span class="btn-text">Tools</span>
        </button>
      </div>
      <div class="toolbar-right">
        <button class="toolbar-btn">
          <span class="btn-icon">🔄</span>
          <span class="btn-text">Change View</span>
        </button>
        <button class="toolbar-btn">
          <span class="btn-icon">▶️</span>
          <span class="btn-text">Run</span>
        </button>
      </div>
    </div>

    <Editor />

    <div class="editor-footer">
      <div class="footer-left">
        <span class="footer-item">HTML</span>
        <span class="footer-item">CSS</span>
        <span class="footer-item">JS</span>
      </div>
      <div class="footer-right">
        <span class="footer-item">Console</span>
        <span class="footer-item">Assets</span>
        <span class="footer-item">⚙️</span>
      </div>
    </div>
  </div>
</template>

<script setup>
import Editor from './Editor.vue';

const emit = defineEmits(['goHome'])

function goToHome() {
  emit('goHome')
}
</script>

<style scoped>
.editor-page {
  display: flex;
  flex-direction: column;
  height: 100vh;
  background-color: #131417;
  color: #fff;
}

.editor-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  height: 60px;
  background-color: #1e1f26;
  border-bottom: 1px solid #2a2b31;
}

.header-left {
  display: flex;
  align-items: center;
  gap: 20px;
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

.pen-title {
  display: flex;
  align-items: center;
}

.title-input {
  background-color: transparent;
  border: 1px solid transparent;
  color: #fff;
  font-size: 16px;
  padding: 5px;
  width: 200px;
}

.title-input:focus {
  border-color: #47cf73;
  outline: none;
}

.header-right {
  display: flex;
  align-items: center;
  gap: 15px;
}

.header-btn {
  background-color: #2a2b31;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  cursor: pointer;
  font-weight: 500;
}

.save-btn {
  background-color: #47cf73;
  color: #131417;
}

.user-menu {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
}

.user-avatar {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background-color: #47cf73;
}

.username {
  font-size: 14px;
}

.editor-toolbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  height: 40px;
  background-color: #1e1f26;
  border-bottom: 1px solid #2a2b31;
}

.toolbar-left, .toolbar-right {
  display: flex;
  gap: 10px;
}

.toolbar-btn {
  background: none;
  border: none;
  color: #a7a9be;
  display: flex;
  align-items: center;
  gap: 5px;
  cursor: pointer;
  padding: 5px 10px;
  border-radius: 4px;
}

.toolbar-btn:hover {
  background-color: #2a2b31;
  color: #fff;
}

.btn-icon {
  font-size: 14px;
}

.btn-text {
  font-size: 14px;
}

.editor-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  height: 40px;
  background-color: #1e1f26;
  border-top: 1px solid #2a2b31;
}

.footer-left, .footer-right {
  display: flex;
  gap: 20px;
}

.footer-item {
  color: #a7a9be;
  font-size: 14px;
  cursor: pointer;
}

.footer-item:hover {
  color: #fff;
}
</style>