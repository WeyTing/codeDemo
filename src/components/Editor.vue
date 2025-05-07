<template>
  <div class="editor-container">
    <div class="editor-header">
      <div class="editor-title">
        <input type="text" placeholder="Untitled Pen" class="title-input" />
        <button class="save-btn">Save</button>
      </div>
      <div class="editor-actions">
        <button class="action-btn">
          <span class="action-icon">⚙️</span>
          Settings
        </button>
        <button class="action-btn">
          <span class="action-icon">🔄</span>
          Change View
        </button>
        <button class="action-btn">
          <span class="action-icon">📤</span>
          Export
        </button>
      </div>
    </div>

    <div class="editor-layout">
      <div class="code-panels">
        <div class="code-panel html-panel">
          <div class="panel-header">
            <div class="panel-title">HTML</div>
            <div class="panel-actions">
              <button class="panel-btn">⚙️</button>
              <button class="panel-btn">🔽</button>
            </div>
          </div>
          <div class="panel-editor">
            <pre class="code-mirror-mock">
<span class="cm-tag">&lt;div</span> <span class="cm-attribute">class</span>=<span class="cm-string">"container"</span><span class="cm-tag">&gt;</span>
  <span class="cm-tag">&lt;h1&gt;</span>Hello, CodePen!<span class="cm-tag">&lt;/h1&gt;</span>
  <span class="cm-tag">&lt;p&gt;</span>This is a sample pen.<span class="cm-tag">&lt;/p&gt;</span>
  <span class="cm-tag">&lt;button</span> <span class="cm-attribute">id</span>=<span class="cm-string">"demo-button"</span><span class="cm-tag">&gt;</span>Click me<span class="cm-tag">&lt;/button&gt;</span>
<span class="cm-tag">&lt;/div&gt;</span>
            </pre>
          </div>
        </div>

        <div class="code-panel css-panel">
          <div class="panel-header">
            <div class="panel-title">CSS</div>
            <div class="panel-actions">
              <button class="panel-btn">⚙️</button>
              <button class="panel-btn">🔽</button>
            </div>
          </div>
          <div class="panel-editor">
            <pre class="code-mirror-mock">
<span class="cm-selector">.container</span> {
  <span class="cm-property">max-width</span>: <span class="cm-number">600px</span>;
  <span class="cm-property">margin</span>: <span class="cm-number">0</span> <span class="cm-atom">auto</span>;
  <span class="cm-property">padding</span>: <span class="cm-number">20px</span>;
  <span class="cm-property">text-align</span>: <span class="cm-atom">center</span>;
  <span class="cm-property">font-family</span>: <span class="cm-string">'Arial'</span>, <span class="cm-atom">sans-serif</span>;
}

<span class="cm-selector">h1</span> {
  <span class="cm-property">color</span>: <span class="cm-atom">#47cf73</span>;
}

<span class="cm-selector">button</span> {
  <span class="cm-property">background</span>: <span class="cm-atom">#47cf73</span>;
  <span class="cm-property">color</span>: <span class="cm-atom">white</span>;
  <span class="cm-property">border</span>: <span class="cm-atom">none</span>;
  <span class="cm-property">padding</span>: <span class="cm-number">10px</span> <span class="cm-number">20px</span>;
  <span class="cm-property">border-radius</span>: <span class="cm-number">4px</span>;
  <span class="cm-property">cursor</span>: <span class="cm-atom">pointer</span>;
  <span class="cm-property">margin-top</span>: <span class="cm-number">20px</span>;
}
            </pre>
          </div>
        </div>

        <div class="code-panel js-panel">
          <div class="panel-header">
            <div class="panel-title">JavaScript</div>
            <div class="panel-actions">
              <button class="panel-btn">⚙️</button>
              <button class="panel-btn">🔽</button>
            </div>
          </div>
          <div class="panel-editor">
            <pre class="code-mirror-mock">
<span class="cm-keyword">const</span> <span class="cm-def">button</span> <span class="cm-operator">=</span> <span class="cm-variable">document</span>.<span class="cm-property">getElementById</span>(<span class="cm-string">'demo-button'</span>);

<span class="cm-variable">button</span>.<span class="cm-property">addEventListener</span>(<span class="cm-string">'click'</span>, () <span class="cm-operator">=></span> {
  <span class="cm-variable">alert</span>(<span class="cm-string">'Button clicked!'</span>);
  <span class="cm-variable">button</span>.<span class="cm-property">textContent</span> <span class="cm-operator">=</span> <span class="cm-string">'Clicked!'</span>;
  <span class="cm-variable">button</span>.<span class="cm-property">style</span>.<span class="cm-property">backgroundColor</span> <span class="cm-operator">=</span> <span class="cm-string">'#3db863'</span>;
});
            </pre>
          </div>
        </div>
      </div>

      <div class="preview-panel">
        <div class="panel-header">
          <div class="panel-title">Result</div>
          <div class="panel-actions">
            <button class="panel-btn">🔄</button>
            <button class="panel-btn">📱</button>
            <button class="panel-btn">⚙️</button>
          </div>
        </div>
        <div class="preview-content">
          <iframe class="preview-iframe"></iframe>
          <div class="preview-placeholder">
            <div class="container">
              <h1>Hello, CodePen!</h1>
              <p>This is a sample pen.</p>
              <button id="demo-button">Click me</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
// Editor component logic can go here
</script>

<style scoped>
.editor-container {
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
  padding: 10px 20px;
  background-color: #1e1f26;
  border-bottom: 1px solid #2a2b31;
}

.editor-title {
  display: flex;
  align-items: center;
  gap: 10px;
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

.save-btn {
  background-color: #47cf73;
  color: #131417;
  border: none;
  border-radius: 4px;
  padding: 5px 15px;
  font-weight: 600;
  cursor: pointer;
}

.editor-actions {
  display: flex;
  gap: 10px;
}

.action-btn {
  background-color: transparent;
  color: #a7a9be;
  border: 1px solid #2a2b31;
  border-radius: 4px;
  padding: 5px 10px;
  display: flex;
  align-items: center;
  gap: 5px;
  cursor: pointer;
}

.action-btn:hover {
  background-color: #2a2b31;
  color: #fff;
}

.action-icon {
  font-size: 14px;
}

.editor-layout {
  display: flex;
  flex-direction: column;
  flex: 1;
  overflow: hidden;
}

@media (min-width: 768px) {
  .editor-layout {
    flex-direction: row;
  }
}

.code-panels {
  display: flex;
  flex-direction: column;
  width: 100%;
  height: 50%;
}

@media (min-width: 768px) {
  .code-panels {
    width: 50%;
    height: 100%;
  }
}

.code-panel {
  flex: 1;
  display: flex;
  flex-direction: column;
  border-right: 1px solid #2a2b31;
  border-bottom: 1px solid #2a2b31;
}

.panel-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 10px;
  background-color: #1e1f26;
  border-bottom: 1px solid #2a2b31;
}

.panel-title {
  font-weight: 600;
  font-size: 14px;
}

.panel-actions {
  display: flex;
  gap: 5px;
}

.panel-btn {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 12px;
  padding: 2px 5px;
}

.panel-editor {
  flex: 1;
  overflow: auto;
  background-color: #1d1e22;
  padding: 10px;
  font-family: 'Consolas', 'Monaco', 'Andale Mono', monospace;
  font-size: 14px;
  line-height: 1.5;
}

.code-mirror-mock {
  margin: 0;
  white-space: pre-wrap;
}

/* Syntax highlighting */
.cm-tag { color: #f92672; }
.cm-attribute { color: #a6e22e; }
.cm-string { color: #e6db74; }
.cm-selector { color: #a6e22e; }
.cm-property { color: #66d9ef; }
.cm-number { color: #ae81ff; }
.cm-atom { color: #ae81ff; }
.cm-keyword { color: #f92672; }
.cm-def { color: #fd971f; }
.cm-variable { color: #f8f8f2; }
.cm-operator { color: #f92672; }
.cm-comment { color: #75715e; }

.preview-panel {
  flex: 1;
  display: flex;
  flex-direction: column;
  height: 50%;
}

@media (min-width: 768px) {
  .preview-panel {
    height: 100%;
  }
}

.preview-content {
  flex: 1;
  background-color: #fff;
  position: relative;
}

.preview-iframe {
  width: 100%;
  height: 100%;
  border: none;
}

.preview-placeholder {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: white;
  color: black;
  overflow: auto;
}

/* Preview content styling */
.preview-placeholder .container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
  font-family: 'Arial', sans-serif;
}

.preview-placeholder h1 {
  color: #47cf73;
}

.preview-placeholder button {
  background: #47cf73;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 20px;
}
</style>