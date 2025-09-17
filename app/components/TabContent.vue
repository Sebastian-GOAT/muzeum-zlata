<template>
    <article class="p-4 flex flex-col gap-2">
        <h1 class="text-lg font-medium">{{ $props.title }}</h1>
        <p class="text-fg-p">
            <slot />
        </p>
    </article>
</template>

<script setup lang="ts">
defineProps<{ title: string; }>();
</script>