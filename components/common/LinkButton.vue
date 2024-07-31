<template>
  <div class="link-button">
    <NuxtLink :to="props.linkTo">{{ props.label }}</NuxtLink>
  </div>
</template>

<script setup lang="ts">
import { onMounted } from "vue";

type LinkButtonProps = {
  label: string;
  linkTo: string;
};

const props = defineProps<LinkButtonProps>();

onMounted(() => {
  console.log(props)
})
</script>

<style>
.link-button {
  @apply max-w-40 max-h-20 p-4 flex items-center justify-center bg-emerald-200 rounded-lg font-bold hover:bg-emerald-400 cursor-pointer;
  border: 1px solid black;
  transition: .3s ease;
}
</style>
