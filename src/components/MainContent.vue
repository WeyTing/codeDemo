<template>
  <div class="main-content">
    <div class="hero-section">
      <h1>CodePen is a <span class="highlight">social development environment</span> for front-end designers and developers.</h1>
      <div class="hero-buttons">
        <button class="sign-up-btn">Sign Up for Free</button>
        <button class="learn-more-btn">Learn More</button>
      </div>
    </div>

    <div class="features-section">
      <h2>Build & Test</h2>
      <div class="features-grid">
        <div class="feature-card" @click="createNewPen">
          <div class="feature-icon">📝</div>
          <h3>Code Editor</h3>
          <p>Write HTML, CSS, and JavaScript. See the results updated in real-time.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon">🧩</div>
          <h3>Front-End Playground</h3>
          <p>Use popular preprocessors like SCSS, Babel, and more.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon">📱</div>
          <h3>Responsive Design Testing</h3>
          <p>Test your designs across different screen sizes.</p>
        </div>
        <div class="feature-card">
          <div class="feature-icon">🔌</div>
          <h3>Add External Resources</h3>
          <p>Use your favorite libraries, frameworks, and APIs.</p>
        </div>
      </div>
    </div>

    <div class="trending-section">
      <div class="section-header">
        <h2>Trending Pens</h2>
        <a href="#" class="view-all">View All</a>
      </div>
      <div class="pens-grid">
        <div class="pen-card" v-for="i in 6" :key="i" @click="createNewPen">
          <div class="pen-preview"></div>
          <div class="pen-info">
            <h4>Amazing CSS Animation</h4>
            <div class="pen-meta">
              <div class="pen-author">
                <div class="author-avatar"></div>
                <span>Username</span>
              </div>
              <div class="pen-stats">
                <span>❤️ 123</span>
                <span>👁️ 456</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const emit = defineEmits(['createPen'])

function createNewPen() {
  emit('createPen')
}
</script>

<style scoped>
.main-content {
  flex: 1;
  padding: 30px;
  background-color: #131417;
  color: #fff;
  overflow-y: auto;
}

.hero-section {
  text-align: center;
  margin-bottom: 60px;
}

.hero-section h1 {
  font-size: 2.5rem;
  max-width: 800px;
  margin: 0 auto 30px;
  line-height: 1.3;
}

.highlight {
  color: #47cf73;
}

.hero-buttons {
  display: flex;
  justify-content: center;
  gap: 15px;
}

.sign-up-btn {
  background-color: #47cf73;
  color: #131417;
  border: none;
  border-radius: 4px;
  padding: 12px 24px;
  font-weight: 600;
  font-size: 16px;
  cursor: pointer;
}

.learn-more-btn {
  background-color: transparent;
  color: #fff;
  border: 1px solid #fff;
  border-radius: 4px;
  padding: 12px 24px;
  font-weight: 600;
  font-size: 16px;
  cursor: pointer;
}

.features-section {
  margin-bottom: 60px;
}

.features-section h2 {
  font-size: 1.8rem;
  margin-bottom: 30px;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 20px;
}

.feature-card {
  background-color: #1e1f26;
  border-radius: 8px;
  padding: 20px;
  transition: transform 0.2s ease;
}

.feature-card:hover {
  transform: translateY(-5px);
}

.feature-icon {
  font-size: 2rem;
  margin-bottom: 15px;
}

.feature-card h3 {
  margin-bottom: 10px;
  font-size: 1.2rem;
}

.feature-card p {
  color: #a7a9be;
  font-size: 0.9rem;
}

.trending-section {
  margin-bottom: 60px;
}

.section-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}

.section-header h2 {
  font-size: 1.8rem;
}

.view-all {
  color: #47cf73;
  text-decoration: none;
}

.pens-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}

.pen-card {
  background-color: #1e1f26;
  border-radius: 8px;
  overflow: hidden;
  transition: transform 0.2s ease;
}

.pen-card:hover {
  transform: translateY(-5px);
}

.pen-preview {
  height: 200px;
  background: linear-gradient(45deg, #3f51b5, #9c27b0);
}

.pen-info {
  padding: 15px;
}

.pen-info h4 {
  margin-bottom: 10px;
  font-size: 1.1rem;
}

.pen-meta {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.pen-author {
  display: flex;
  align-items: center;
  gap: 8px;
}

.author-avatar {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background-color: #47cf73;
}

.pen-stats {
  display: flex;
  gap: 10px;
  color: #a7a9be;
  font-size: 0.8rem;
}
</style>