<template>
  <div class="header-container">
    <div>GNB</div>
    <div class="header-button-section">
      <LinkButton :label="'갤러리'" link-to="/gallery" />
      <LinkButton :label="'홈'" link-to="/" />
    </div>
  </div>
</template>
    
<script setup lang="ts">
import LinkButton from "../common/LinkButton.vue";
</script>
    
<style>
.header-container {
  @apply flex items-center justify-between w-full h-full bg-slate-200 p-3;
}

.header-button-section {
  @apply flex items-center justify-center gap-4;
}
</style>