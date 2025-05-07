<template>
  <div class="editor-container">
    <div class="editor-header">
      <div class="editor-title">
        <input
          type="text"
          placeholder="Untitled Pen"
          class="title-input"
          v-model="penTitle"
        />
        <button class="save-btn" @click="updatePreview">Run</button>
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
          <div class="panel-editor" ref="htmlEditorContainer"></div>
        </div>

        <div class="code-panel css-panel">
          <div class="panel-header">
            <div class="panel-title">CSS</div>
            <div class="panel-actions">
              <button class="panel-btn">⚙️</button>
              <button class="panel-btn">🔽</button>
            </div>
          </div>
          <div class="panel-editor" ref="cssEditorContainer"></div>
        </div>

        <div class="code-panel js-panel">
          <div class="panel-header">
            <div class="panel-title">JavaScript</div>
            <div class="panel-actions">
              <button class="panel-btn">⚙️</button>
              <button class="panel-btn">🔽</button>
            </div>
          </div>
          <div class="panel-editor" ref="jsEditorContainer"></div>
        </div>
      </div>

      <div class="preview-panel">
        <div class="panel-header">
          <div class="panel-title">Result</div>
          <div class="panel-actions">
            <button class="panel-btn" @click="updatePreview">🔄</button>
            <button class="panel-btn">📱</button>
            <button class="panel-btn">⚙️</button>
          </div>
        </div>
        <div class="preview-content">
          <iframe class="preview-iframe" ref="previewFrame"></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import { EditorState } from "@codemirror/basic-setup";
import { EditorView, keymap } from "@codemirror/view";
import { defaultKeymap } from "@codemirror/commands";
import { html } from "@codemirror/lang-html";
import { css } from "@codemirror/lang-css";
import { javascript } from "@codemirror/lang-javascript";

// 初始代碼
const initialHtml = `<div class="container">
  <h1>Hello, CodePen!</h1>
  <p>This is a sample pen.</p>
  <button id="demo-button">Click me</button>
</div>`;

const initialCss = `.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  text-align: center;
  font-family: 'Arial', sans-serif;
}

h1 {
  color: #47cf73;
}

button {
  background: #47cf73;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 4px;
  cursor: pointer;
  margin-top: 20px;
}`;

const initialJs = `const button = document.getElementById('demo-button');

button.addEventListener('click', () => {
  alert('Button clicked!');
  button.textContent = 'Clicked!';
  button.style.backgroundColor = '#3db863';
});`;

// 編輯器引用
const htmlEditorContainer = ref(null);
const cssEditorContainer = ref(null);
const jsEditorContainer = ref(null);
const previewFrame = ref(null);
const penTitle = ref("Untitled Pen");

// 編輯器實例
let htmlEditor = null;
let cssEditor = null;
let jsEditor = null;

// 創建編輯器
function createEditor(container, language, initialValue) {
  const languageSupport =
    language === "html" ? html() : language === "css" ? css() : javascript();

  const state = EditorState.create({
    doc: initialValue,
    extensions: [
      keymap.of(defaultKeymap),
      languageSupport,
      EditorView.contentAttributes.of({ contenteditable: "true" }),
      EditorView.lineWrapping,
      EditorView.theme({
        "&": {
          backgroundColor: "#1d1e22",
          color: "#f8f8f2",
          height: "100%",
        },
        ".cm-content": {
          caretColor: "#f8f8f2",
          padding: "10px",
        },
        "&.cm-focused .cm-cursor": {
          borderLeftColor: "#f8f8f2",
        },
        "&.cm-focused .cm-selectionBackground, .cm-selectionBackground, .cm-content ::selection":
          {
            backgroundColor: "#44475a",
          },
        ".cm-gutters": {
          backgroundColor: "#1d1e22",
          color: "#6D8A88",
          border: "none",
        },
      }),
    ],
  });

  return new EditorView({
    state,
    parent: container,
  });
}

// 更新預覽
function updatePreview() {
  console.log("Updating preview");
  if (!previewFrame.value || !htmlEditor || !cssEditor || !jsEditor) {
    console.log("Missing required elements for preview");
    return;
  }

  try {
    const htmlContent = htmlEditor.state.doc.toString();
    const cssContent = cssEditor.state.doc.toString();
    const jsContent = jsEditor.state.doc.toString();

    const iframe = previewFrame.value;
    const iframeDoc = iframe.contentDocument || iframe.contentWindow.document;
    iframeDoc.open();
    iframeDoc.write(previewContent);
    iframeDoc.close();
  } catch (error) {
    console.error("Error updating preview:", error);
  }
}

// 生命週期鉤子
onMounted(() => {
  console.log("Component mounted");
  try {
    // 創建編輯器
    console.log("Creating editors");
    htmlEditor = createEditor(htmlEditorContainer.value, "html", initialHtml);
    cssEditor = createEditor(cssEditorContainer.value, "css", initialCss);
    jsEditor = createEditor(jsEditorContainer.value, "javascript", initialJs);

    console.log("Editors created:", htmlEditor, cssEditor, jsEditor);
  } catch (error) {
    console.error("Error creating editors:", error);
  }
});

onUnmounted(() => {
  // 清理編輯器
  if (htmlEditor) htmlEditor.destroy();
  if (cssEditor) cssEditor.destroy();
  if (jsEditor) jsEditor.destroy();
});
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
}

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
</style>
