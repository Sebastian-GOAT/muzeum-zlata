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
            class="p-4 w-[700px] max-w-9/10 border-1 border-black/30 dark:border-white/30 rounded-lg"
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

    <!-- Usage, images -->
    <section class="px-16 py-12 flex flex-col gap-24 justify-center items-center">
        <div class="w-128 max-w-9/10 text-lg text-fg-p leading-8">
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
            auto-scroll
            class="w-[650px] max-w-full"
            :items="images"
            :ui="{ item: 'basis-1/3' }"
        >
            <NuxtImg :src="item" width="234" height="234" class="rounded-lg" />
        </UCarousel>
    </section>

    <!-- Heading -->
    <Heading title="Světoví těžitelé" />

    <!-- Top global miners -->
    <section class="px-16 py-12 flex justify-center items-center">
        <div class="w-128 max-w-9/10 text-lg text-fg-p leading-8 flex flex-col gap-12 justify-center items-center">
            <p>
                5 největších světových těžitelů:
            </p>
            <NuxtImg
                src="/chart.png"
                class="w-[min(500px,_80%)] rounded-2xl border-1 border-black"
                alt="Graf světových těžitelů"
                
            />
            <UTable :data="globalMinersData" class="w-full" />
        </div>
    </section>

    <!-- Heading -->
    <Heading title="Ekologické dopady a recyklace" />

    <!-- Eco -->
    <section class="px-16 py-12 flex justify-center items-center">
        <p class="w-128 max-w-9/10 text-lg text-fg-p leading-8">
            Při těžbě se často používají toxické chemikálie, což může způsobovat emise a škodu
            okolní přírodě. Emise jsou také způsobené náročností těžby.
            <br><br>
            Recyklovat je důležité pro ochranu přírody a zachování globální hodnoty zlata. Zlato
            lze recyklovat skoro bez ztráty ceny. Lze tím také vydělat na použitém/starým zlatem
        </p>
    </section>

</template>

<script setup lang="ts">
definePageMeta({
    layout: 'default'
});

useHead({
    title: 'Muzeum zlata',
    meta: [
        { name: 'description', content: 'Virtuální muzeum zlata – objevte jeden z nejvzácnějších kovů světa. Interaktivní online expozice pro osobní poznání.' }
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

const propertiesTableData = [{
    'Značka': 'Au',
    'Hustota': '19.32g/cm^2',
    'Bod tání': '1064°C',
    'Bod varu': '2856°C'
}];

const images = [
  '/gold_bars.png',
  '/craiyon_1.png',
  '/craiyon_2.png',
  '/craiyon_3.png',
  '/gold_drawing_1.jpg'
];

const globalMinersData = [
    {
        'Společnost': 'Barrick Gold Corporation (Kanada)',
        'Produkce': '4 700 000 oz/rok'
    },
    {
        'Společnost': 'Newmont Corporation (USA)',
        'Produkce': '6 000 000 oz/rok'
    },
    {
        'Společnost': 'AngloGold Ashanti (Jižní Afrika)',
        'Produkce': '3 000 000 oz/rok'
    },
    {
        'Společnost': 'China National Gold Group (Čína)',
        'Produkce': '2 500 000 oz/rok'
    },
    {
        'Společnost': 'Polyus Gold (Rusko)',
        'Produkce': '2 800 000 oz/rok'
    }
];
</script>