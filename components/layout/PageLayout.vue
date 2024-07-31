<template>
  <div class="page-container">
    <div class="page-header-container">
      <slot name="page-header"></slot>
    </div>
    <div class="page-body-container">
      <slot name="page-body"></slot>
    </div>
    <div class="page-footer-container">
      <slot name="page-footer"></slot>
    </div>
  </div>
</template>
  
<script setup lang="ts">
</script>
  
<style>
.page-container {
  @apply w-screen h-screen p-4;
}

.page-header-container {
  @apply bg-slate-400;
}

.page-body-container {
  @apply bg-red-200;
}

.page-footer-container {
  @apply bg-green-200;
}
</style>