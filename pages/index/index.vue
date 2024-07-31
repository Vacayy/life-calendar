<template>
  <PageLayout>
    <template v-slot:page-header>
      <PageHeader />
    </template>
    <template v-slot:page-body>
      <NuxtPage />
    </template>
    <template v-slot:page-footer>
    </template>
  </PageLayout>
</template>

<script setup lang="ts">
import PageLayout from "~/components/layout/PageLayout.vue";
import PageHeader from "~/components/layout/PageHeader.vue";
</script>

<style>
</style>