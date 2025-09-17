<template>
    <section class="px-16 py-8 flex justify-center">
        <h1 class="text-4xl text-center font-medium underline underline-offset-6">{{ $props.title }}</h1>
    </section>
</template>

<script setup lang="ts">
defineProps<{
    title: string;
}>();
</script>