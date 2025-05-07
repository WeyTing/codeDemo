<script setup>
import { ref } from 'vue'
import Sidebar from './components/Sidebar.vue'
import Header from './components/Header.vue'
import MainContent from './components/MainContent.vue'
import EditorPage from './components/EditorPage.vue'

const currentView = ref('home') // 'home' or 'editor'

function switchToEditor() {
  currentView.value = 'editor'
}

function switchToHome() {
  currentView.value = 'home'
}
</script>

<template>
  <div v-if="currentView === 'home'" class="app-container">
    <Sidebar />
    <div class="content-wrapper">
      <Header @createPen="switchToEditor" />
      <MainContent @createPen="switchToEditor" />
    </div>
  </div>
  <EditorPage v-else @goHome="switchToHome" />
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  background-color: #131417;
  color: #fff;
}

.app-container {
  display: flex;
  height: 100vh;
  overflow: hidden;
}

.content-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  overflow: hidden;
}
</style>