<template>
    
    <!-- Hero section -->
    <section class="h-fit lg:h-[600px] flex flex-col lg:flex-row">

        <div class="px-24 py-16 w-full lg:w-3/7 lg:h-full flex justify-center items-center">
            <div class="flex flex-col gap-8 text-center lg:text-start">
                <h1 class="text-6xl font-semibold">Interaktivní muzeum zlata</h1>
                <p class="text-lg text-fg-p leading-10">
                    Zlato – symbol bohatství a krásy.
                    Prozkoumejte ho do hloubky a objevte
                    jeho tajemství v našem interaktivním
                    muzeu.
                </p>
            </div>
        </div>

        <div class="h-80 lg:h-full flex lg:flex-1 justify-center items-center relative">
            <NuxtImg
                src="/gold_bars.png"
                alt="Gold bars"
                class="lg:w-100 lg:max-w-2/3 h-3/4 lg:h-auto"
            />
            <!-- Golden glow -->
            <div class="absolute top-1/2 left-1/2 -translate-1/2 -z-1 w-72 h-72 bg-yellow-500 blur-2xl opacity-40 rounded-full" />
        </div>

    </section>

    <!-- Heading -->
    <Heading title="O zlatu" />

    <!-- Properties -->
    <section class="px-16 py-12 flex justify-center">
        <UTabs
            :items="propertiesData"
            class="p-4 w-[700px] border-1 border-muted rounded-lg"
            variant="link"
            color="primary"
        >

            <template #popis="{ item }">
                <TabContent :title="item.label">
                    Zlato je měkčí ozdobný kov s naoranžovělým odstínem žluté (tzv. zlatá). Díky své vzácnosti je velice drahý a jeho hodnota pořád roste.
                </TabContent>
            </template>

            <template #vlastnosti="{ item }">
                <TabContent :title="item.label">
                    <UTable :data="propertiesTableData" class="flex-1" />
                </TabContent>
            </template>

        </UTabs>
    </section>

    <!-- Heading -->
    <Heading title="Využití" />

    <!-- Usage, AI generated images -->
    <section class="px-16 py-12 flex flex-col gap-24 justify-center items-center">
        <div class="w-128 text-lg text-fg-p leading-8">
            <p>
                Zlato se používá k výrobě různých věcí. Nejčastěji se jedná o jeden z následujících produktů:
            </p>
            <br>
            <ul class="list-disc list-inside">
                <li>Šperky (náhrdelníky, prstýnky, hodinky apod.)</li>
                <li>Mince (dnes se spíše používá levnější kov)</li>
                <li>Ozdoby (Pozlacení budov, lustry, občas se dává i na jídlo)</li>
                <li>Elektronické součástky</li>
            </ul>
        </div>
        <UCarousel
            v-slot="{ item }"
            loop
            arrows
            dots
            class="w-[650px]"
            :autoplay="{ delay: 2000 }"
            :items="AIPictures"
            :ui="{ item: 'basis-1/3' }"
        >
            <NuxtImg :src="item" width="234" height="234" class="rounded-lg" />
        </UCarousel>
    </section>

</template>

<script setup lang="ts">
definePageMeta({
    layout: 'default'
});

useHead({
    title: 'Muzeum zlata',
    meta: [
        { name: 'description', content: 'Virtuální muzeum zlata – objevte historii, využití a fascinující příběhy jednoho z nejvzácnějších kovů světa. Interaktivní expozice pro školní i osobní poznání.' }
    ]
});

import type { TabsItem } from '@nuxt/ui';

const propertiesData = [
    {
        label: 'Popis',
        icon: 'i-lucide-user',
        slot: 'popis' as const,
        htmlContent: ''
    },
    {
        label: 'Fyzikální vlastnosti',
        icon: 'i-lucide-user',
        slot: 'vlastnosti' as const,
        htmlContent: ''
    }
] satisfies TabsItem[];

const propertiesTableData = ref([{
    'Značka': 'Au',
    'Hustota': '19.32g/cm^2',
    'Bod tání': '1064°C',
    'Bod varu': '2856°C'
}]);

const AIPictures = [
  'https://picsum.photos/468/468?random=1',
  'https://picsum.photos/468/468?random=2',
  'https://picsum.photos/468/468?random=3',
  'https://picsum.photos/468/468?random=4',
  'https://picsum.photos/468/468?random=5',
  'https://picsum.photos/468/468?random=6'
];
</script>