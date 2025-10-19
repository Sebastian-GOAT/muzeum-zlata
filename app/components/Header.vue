<template>
    
    <header class="px-8 h-16 flex justify-between items-center">

        <!-- Logo -->
        <NuxtLink to="/" class="font-extrabold italic">
            Muzeum Zlata
        </NuxtLink>
        <div class="flex gap-2 items-center">
            <Icon :name="isDark ? 'uil:moon' : 'uil:sun'" size="22" />
            <USwitch
                color="primary"
                v-model="isDark"
            />
        </div>

    </header>

</template>

<script setup lang="ts">
const colorMode = useColorMode();
const isDark = ref(false);

onMounted(() => isDark.value = colorMode.value === 'dark');
watch(isDark, newVal => colorMode.preference = newVal ? 'dark' : 'light');
</script>