<template>
    
    <header class="px-8 h-16 flex justify-between items-center">

        <!-- Logo -->
        <NuxtLink to="/" class="font-extrabold italic">
            Logo
        </NuxtLink>
        <div class="flex gap-2 items-center">
            <Icon name="uil:moon" size="22" />
            <USwitch
                color="primary"
                v-model="isDark"
            />
        </div>

    </header>

</template>

<script setup lang="ts">
const isDark = ref(true);
const colorMode = useColorMode();

onMounted(() => isDark.value = colorMode.preference === 'dark');
watch(isDark, newVal => colorMode.preference = newVal ? 'dark' : 'light');
</script>