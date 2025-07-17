<template>
  <div class="pdf-ai-assistant-unified">
    <h1 class="title">📄 PDF AI Assistant</h1>
    <p class="subtitle">✨ Instantly summarize, analyze, and simplify your PDFs with AI—tailored to your document type.</p>
    <p class="description">🔹 Upload a PDF, provide context, choose tasks, and download your personalized report.</p>

    <div class="workflow-steps">
      <!-- Step 1: Upload PDF -->
      <div class="workflow-step">
        <h2>📤 Step 1: Upload Your PDF</h2>
        <UploadForm @file-uploaded="onFileUploaded" />
        <div class="step-subtext">Supported formats: <b>PDF only</b>. Max size: <b>10MB</b></div>
      </div>
      <div class="workflow-divider"></div>

      <!-- Step 2: Add Context -->
      <div class="workflow-step">
        <h2>🧠 Step 2: Add Context <span class="optional">(Optional but Helpful)</span></h2>
        <ContextInput />
        <div class="step-subtext">
          Adding context helps the AI generate more relevant and accurate outputs.
        </div>
      </div>
      <div class="workflow-divider"></div>

      <!-- Step 3: Select Document Type -->
      <div class="workflow-step">
        <h2>📂 Step 3: Select Document Type</h2>
        <DocumentTypeSelector v-model:selectedType="selectedType" />
        <div class="step-subtext">
          AI uses this to apply the right tone, analysis depth, and formatting.
        </div>
      </div>
      <div class="workflow-divider"></div>

      <!-- Step 4: Choose AI Tasks -->
      <div class="workflow-step">
        <h2>✅ Step 4: Choose AI Tasks</h2>
        <AiTaskSelector v-model:selectedTask="selectedTask" />
        <div class="step-subtext">
          Pre-written prompts (placeholders for now) will tailor the results to your needs.
        </div>
      </div>
      <div class="workflow-divider"></div>

      <!-- Step 5: Generate Report -->
      <div class="workflow-step">
        <h2>🚀 Step 5: Generate Your AI Report</h2>
        <GenerateButton :disabled="!canGenerate" @click="onGenerate" />
        <div class="step-subtext">
          Your final report will be generated as a downloadable PDF.
        </div>
      </div>
      <div class="workflow-divider"></div>

      <!-- Processing Status -->
      <div class="workflow-step" v-if="showProcessing">
        <ProcessingStatus />
      </div>
      <div class="workflow-divider"></div>

      <!-- Download Report -->
      <div class="workflow-step">
        <DownloadReport />
        <div class="step-subtext">
          Summary of included features based on selected checkboxes
        </div>
      </div>
    </div>

    <!-- Footer -->
    <footer class="footer">
      <div class="footer-links">
        <a href="#">Privacy Policy</a> |
        <a href="#">Terms of Use</a> |
        <a href="#">Contact</a>
      </div>
      <div class="footer-tagline">
        AI-enhanced document understanding. Fast, simple, personalized.
      </div>
    </footer>
  </div>
</template>

<script>
import UploadForm from '../components/UploadForm.vue';
import ContextInput from '../components/ContextInput.vue';
import DocumentTypeSelector from '../components/DocumentTypeSelector.vue';
import AiTaskSelector from '../components/AiTaskSelector.vue';
import GenerateButton from '../components/GenerateButton.vue';
import ProcessingStatus from '../components/ProcessingStatus.vue';
import DownloadReport from '../components/DownloadReport.vue';

export default {
  name: 'PdfAiAssistant',
  components: {
    UploadForm,
    ContextInput,
    DocumentTypeSelector,
    AiTaskSelector,
    GenerateButton,
    ProcessingStatus,
    DownloadReport,
  },
  data() {
    return {
      selectedTask: '',
      uploadedFile: null,
      showProcessing: false,
      selectedType: '',
    };
  },
  computed: {
    canGenerate() {
      return !!this.uploadedFile && !!this.selectedTask && !!this.selectedType;
    },
  },
  methods: {
    onFileUploaded(file) {
      this.uploadedFile = file;
    },
    onGenerate() {
      if (!this.canGenerate) return;
      this.showProcessing = true;
      // Simulate processing (replace with real API call later)
      setTimeout(() => {
        this.showProcessing = false;
      }, 3000);
    },
  },
};
</script>

<style scoped>
.pdf-ai-assistant-unified {
  max-width: 800px;
  margin: 2.5rem auto 1.5rem auto;
  padding: 2.5rem 2.5rem 1.5rem 2.5rem;
  background: #181a20;
  border-radius: 18px;
  text-align: center;
  box-shadow: none;
  border: 1.5px solid #23242a;
}
.title {
  font-size: 2.1rem;
  margin-bottom: 0.5rem;
  color: #fff;
  font-weight: 700;
  letter-spacing: -1px;
}
.subtitle {
  font-size: 1.08rem;
  color: #b3b3b3;
  margin-bottom: 0.5rem;
  font-weight: 400;
}
.description {
  font-size: 1rem;
  color: #888;
  margin-bottom: 2rem;
  font-weight: 400;
}
.workflow-steps {
  display: flex;
  flex-direction: column;
  gap: 0;
  background: none;
}
.workflow-step {
  padding: 1.1rem 0.5rem 0.7rem 0.5rem;
  text-align: left;
}
.workflow-step h2 {
  font-size: 1.08rem;
  margin-bottom: 0.7rem;
  color: #e0e0e0;
  font-weight: 600;
}
.workflow-divider {
  height: 1px;
  background: #23242a;
  margin: 0.1rem 0 0.1rem 0;
  width: 100%;
  border: none;
}
.optional {
  font-size: 0.92em;
  color: #888;
}
.step-subtext {
  font-size: 0.97em;
  color: #666;
  margin-top: 0.5rem;
}
.footer {
  margin-top: 2.5rem;
  padding-top: 1.5rem;
  border-top: 1px solid #23242a;
  color: #888;
  font-size: 0.97em;
  background: transparent;
}
.footer-links a {
  color: #8a8cff;
  margin: 0 0.3em;
  text-decoration: none;
  font-weight: 500;
}
.footer-links a:hover {
  text-decoration: underline;
  color: #b3b3ff;
}
.footer-tagline {
  margin-top: 0.5rem;
  color: #666;
}

@media (max-width: 900px) {
  .pdf-ai-assistant-unified {
    max-width: 98vw;
    padding: 1.2rem 0.5rem 0.7rem 0.5rem;
  }
  .workflow-step {
    padding: 0.8rem 0.1rem 0.5rem 0.1rem;
  }
}
</style>
