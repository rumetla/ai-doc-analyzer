<template>
  <div class="download-report">
    <button class="download-btn" disabled>
      📥 Download Report
    </button>
    <div class="download-summary">
      (Summary of included features based on selected checkboxes)
    </div>
  </div>
</template>

<script>
export default {
  name: 'DownloadReport',
};
</script>

<style scoped>
.download-report {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.7rem;
}
.download-btn {
  width: 100%;
  padding: 1em 0;
  font-size: 1.08em;
  font-weight: 600;
  background: #23242a;
  color: #fff;
  border: 1px solid #23242a;
  border-radius: 10px;
  cursor: not-allowed;
  opacity: 0.8;
  margin-bottom: 0.3em;
  box-shadow: 0 2px 8px 0 rgba(0,0,0,0.10);
}
.download-summary {
  font-size: 0.98em;
  color: #666;
  text-align: center;
}
</style>
