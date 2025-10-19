<template>
    <UApp>
        <NuxtLayout>
            <NuxtPage />
        </NuxtLayout>
    </UApp>
</template>

<style>
@import "tailwindcss";
@import "@nuxt/ui";

:root {
    --primary: #00dc82;
    --secondary: #51A1FE;

    --bg: hsl(0, 0%, 100%);
    --fg: black;
    --fg-p: hsl(0, 0%, 25%);
}

.dark {
    --bg: #0f172b;
    --fg: white;
    --fg-p: hsl(0, 0%, 75%);
}

@theme inline {
    --color-bg: var(--bg);
    --color-fg: var(--fg);
    --color-fg-p: var(--fg-p);
    --color-primary: var(--primary);
    --color-secondary: var(--secondary);
}

body {
    min-height: 100vh;

    background-color: var(--bg);
    color: var(--fg);
}
</style>