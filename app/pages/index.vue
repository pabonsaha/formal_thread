<script setup lang="ts">
import AppFooter from '~/components/AppFooter.vue'

const serviceItems = [
  'Free delivery',
  'Money back guarantee',
  '24/7 support',
  'High quality cotton',
]

const saleTabs = ['Women', 'Men', 'Kids', 'Accessories']

const categoryTiles = [
  {
    label: 'Women',
    position: '0% center',
  },
  {
    label: 'Men',
    position: '33.333% center',
  },
  {
    label: 'Kids',
    position: '66.666% center',
  },
  {
    label: 'Accessories',
    position: '100% center',
  },
]

const saleProducts = [
  {
    brand: 'Prada',
    name: 'Crossback Halter Dress',
    description: 'A shapely halter dress designed with slinky crossback straps and a leg-baring slit is an elegant option for your upcoming event.',
    price: '$2,400.00',
    priceRange: '$2,400.00 - $2,650.00',
    imagePosition: '10% top',
    imageSize: '305% auto',
    imageAlt: 'Model wearing a black crossback halter dress',
    badges: [
      { label: 'Best Seller' },
      { label: '-4%', tone: 'sale' as const },
    ],
    colors: [
      { name: 'Black', value: '#050505' },
      { name: 'Navy', value: '#17405f' },
      { name: 'Brown', value: '#4a240d' },
    ],
  },
  {
    brand: 'Valentino',
    name: 'V Logo Pocket Wool & Silk Dress',
    description: 'A pair of pockets is often the best thing a dress can offer, and when they appear with the iconic Valentino logo, they really reach perfection.',
    price: '$6,500.00',
    compareAt: '$7,500.00',
    imagePosition: '48% top',
    imageSize: '305% auto',
    imageAlt: 'Model wearing a white short sleeve dress',
    badges: [
      { label: '-13%', tone: 'sale' as const },
    ],
  },
  {
    brand: 'Bottega Veneta',
    name: 'Sequin Textured Knit A-Line Gown',
    description: 'Shimmering sequins illuminate the textured knit of this occasion-worthy gown in a simply elegant A-line cut.',
    price: '$6,500.00',
    compareAt: '$7,000.00',
    imagePosition: '50% top',
    imageSize: '245% auto',
    imageAlt: 'Model wearing a sequin textured A-line gown',
    badges: [
      { label: '-7%', tone: 'sale' as const },
    ],
  },
  {
    brand: 'Fendi',
    name: 'Melody Fleece Pullover Sweatshirt',
    description: 'An adjustable drawstring cinches the wide hemline of this comfort-first fleece pullover with a slouchy turtleneck and thumbhole cuffs.',
    price: '$850.00',
    compareAt: '$900.00',
    imagePosition: '100% top',
    imageSize: '300% auto',
    imageAlt: 'Model wearing a dark fleece pullover sweatshirt',
    badges: [
      { label: '-6%', tone: 'sale' as const },
      { label: 'Featured' },
    ],
  },
  {
    brand: 'Frame',
    name: 'Le Cutoff Denim Shorts',
    description: 'A relaxed fit boosts the laid-back vibe.',
    price: '$100.00',
    compareAt: '$150.00',
    imagePosition: '88% top',
    imageSize: '235% auto',
    imageAlt: 'Model wearing black cutoff denim shorts',
    badges: [
      { label: '-33%', tone: 'sale' as const },
    ],
    stock: {
      sold: 9,
      available: 11,
    },
  },
]
</script>

<template>
  <main class="bg-white text-black">
    <section class="grid min-h-[calc(100vh-111px)] border-b border-black lg:grid-cols-3">
      <div class="relative flex min-h-[560px] flex-col justify-center px-6 py-16 sm:px-10 lg:min-h-0 lg:px-[70px]">
        <div class="max-w-[520px]">
          <h1 class="text-[clamp(48px,5vw,72px)] font-normal leading-[0.94] tracking-0">
            New Spring<br>
            Collection 2023
          </h1>

          <p class="mt-8 max-w-[545px] text-sm leading-7 text-black">
            Introducing our new spring fashion collection, perfect for effortless casual
            chic. From flowy dresses to floral tops, mix and match with ease. Lightweight
            fabrics and cheerful colors to awaken the Spring in you.
          </p>

          <NuxtLink
            to="/shop"
            class="mt-8 inline-flex h-[50px] min-w-[170px] items-center justify-center bg-black px-8 text-xs font-bold uppercase text-white transition-colors hover:bg-gray"
          >
            Shop now
          </NuxtLink>
        </div>

        <div class="absolute bottom-12 left-6 flex items-center gap-3 sm:left-10 lg:left-[70px]">
          <button class="slider-dot slider-dot-active" type="button" aria-label="Go to slide 1" />
          <button class="slider-dot" type="button" aria-label="Go to slide 2" />
          <button class="slider-dot" type="button" aria-label="Go to slide 3" />
        </div>
      </div>

      <div class="hero-panel hero-panel-center min-h-[560px]" aria-label="Spring collection models" />
      <div class="hero-panel hero-panel-right hidden min-h-[560px] lg:block" aria-label="White knit dress detail" />
    </section>

    <section class="overflow-hidden border-b border-black bg-white py-6" aria-label="Store benefits">
      <div class="marquee-track flex w-max items-center gap-5">
        <template v-for="repeat in 3" :key="repeat">
          <template v-for="item in serviceItems" :key="`${repeat}-${item}`">
            <span class="text-sm font-bold uppercase tracking-0">{{ item }}</span>
            <span class="text-sm font-bold" aria-hidden="true">·</span>
          </template>
        </template>
      </div>
    </section>

    <section class="bg-white px-4 pb-14 pt-14 sm:px-8 lg:px-12" aria-labelledby="big-sales-title">
      <div class="mx-auto max-w-[1536px]">
        <div class="mb-8 text-center">
          <h2 id="big-sales-title" class="text-[28px] font-black uppercase leading-none tracking-0">
            Big Sales
          </h2>

          <div class="mt-8 flex items-center justify-center gap-9 overflow-x-auto" role="tablist" aria-label="Sale categories">
            <button
              v-for="(tab, index) in saleTabs"
              :key="tab"
              class="sale-tab"
              :class="{ 'sale-tab-active': index === 0 }"
              type="button"
              role="tab"
              :aria-selected="index === 0"
            >
              {{ tab }}
            </button>
          </div>
        </div>

        <div class="border-y border-black/15">
          <div class="grid sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5">
            <ProductCard
              v-for="product in saleProducts"
              :key="product.name"
              :product="product"
            />
          </div>
        </div>

        <div class="mt-7 flex items-center justify-center gap-4" aria-label="Product carousel pagination">
          <button class="slider-dot slider-dot-active" type="button" aria-label="Go to product slide 1" />
          <button class="slider-dot" type="button" aria-label="Go to product slide 2" />
        </div>
      </div>
    </section>

    <section class="brand-statement relative overflow-hidden border-t border-black bg-white px-5 py-20 sm:px-8 lg:py-[92px]" aria-label="Brand statement">
      <Icon
        class="brand-statement-mark"
        name="lucide:flower-2"
        aria-hidden="true"
      />

      <p class="brand-statement-copy mx-auto max-w-[1530px] text-center text-[clamp(34px,2.45vw,48px)] font-normal leading-[1.58] tracking-0 text-black">
        We believe that every human deserves to feel beautiful and confident, and we
        are committed to providing you with the best quality and styles that will make
        you look and feel your best.
      </p>
    </section>

    <section class="category-strip grid border-y border-black bg-white sm:grid-cols-2 lg:grid-cols-4" aria-label="Shop by category">
      <NuxtLink
        v-for="category in categoryTiles"
        :key="category.label"
        to="/shop"
        class="category-tile group relative flex min-h-[420px] items-center justify-center overflow-hidden border-black sm:min-h-[520px] lg:min-h-[650px]"
      >
        <span
          class="category-tile-image absolute inset-0 bg-cover bg-center transition-transform duration-500 group-hover:scale-[1.04]"
          :style="{ backgroundPosition: category.position }"
          aria-hidden="true"
        />

        <span class="relative z-10 inline-flex min-h-[52px] min-w-[156px] items-center justify-center bg-white px-8 text-base font-black uppercase leading-none tracking-0 text-black transition-colors group-hover:bg-black group-hover:text-white">
          {{ category.label }}
        </span>
      </NuxtLink>
    </section>
  </main>

  <AppFooter />
</template>

<style scoped>
.tracking-0 {
  letter-spacing: 0;
}

.hero-panel {
  background-image: url('/spring-collection-reference.png');
  background-repeat: no-repeat;
  background-size: 300% auto;
}

.hero-panel-center {
  background-position: 50% top;
}

.hero-panel-right {
  background-position: 100% top;
}

.slider-dot {
  width: 5px;
  height: 5px;
  border-radius: 999px;
  background: var(--color-gray);
  opacity: 0.35;
}

.slider-dot-active {
  position: relative;
  background: var(--color-black);
  opacity: 1;
}

.slider-dot-active::before {
  position: absolute;
  inset: -4px;
  content: "";
  border: 1px solid var(--color-black);
  border-radius: 999px;
}

.sale-tab {
  position: relative;
  flex: 0 0 auto;
  padding-bottom: 10px;
  color: var(--color-gray);
  font-size: 13px;
  font-weight: 800;
  line-height: 1;
  letter-spacing: 0;
  text-transform: uppercase;
  transition: color 160ms ease;
}

.sale-tab:hover,
.sale-tab-active {
  color: var(--color-black);
}

.sale-tab-active::after {
  position: absolute;
  right: 0;
  bottom: 0;
  left: 0;
  height: 1px;
  content: "";
  background: var(--color-black);
}

.marquee-track {
  animation: marquee 28s linear infinite;
}

.brand-statement {
  min-height: 515px;
}

.brand-statement-copy {
  position: relative;
  z-index: 1;
}

.brand-statement-mark {
  position: absolute;
  top: 52%;
  left: 50%;
  width: min(430px, 62vw);
  height: min(430px, 62vw);
  color: var(--color-gray);
  opacity: 0.28;
  transform: translate(-50%, -50%);
  pointer-events: none;
}

.category-tile {
  border-bottom-width: 1px;
}

.category-tile-image {
  background-image: url('/category-strip-reference.png');
  background-size: 400% 100%;
}

@keyframes marquee {
  from {
    transform: translateX(0);
  }

  to {
    transform: translateX(-33.333%);
  }
}

@media (max-width: 1023px) {
  .hero-panel {
    min-height: 520px;
    background-size: 190% auto;
    background-position: center top;
  }

  .category-tile:nth-child(odd) {
    border-right-width: 1px;
  }
}

@media (max-width: 767px) {
  .hero-panel {
    min-height: 430px;
    background-size: 230% auto;
  }

  .brand-statement {
    min-height: 420px;
  }

  .brand-statement-copy {
    line-height: 1.35;
  }

  .brand-statement-mark {
    width: 340px;
  }

  .category-tile {
    border-right-width: 0;
  }
}

@media (min-width: 1024px) {
  .category-tile {
    border-bottom-width: 0;
  }

  .category-tile:not(:last-child) {
    border-right-width: 1px;
  }
}
</style>
