<script setup lang="ts">
import AppFooter from '~/components/AppFooter.vue'
import ProductCard from '~/components/ProductCard.vue'

type ProductBadgeTone = 'dark' | 'sale'

interface ProductBadge {
  label: string
  tone?: ProductBadgeTone
}

interface ProductColor {
  name: string
  value: string
}

interface ProductStock {
  sold: number
  available: number
}

interface Product {
  brand: string
  name: string
  description: string
  price: string
  compareAt?: string
  priceRange?: string
  imagePosition: string
  imageSize?: string
  imageAlt: string
  badges?: ProductBadge[]
  colors?: ProductColor[]
  stock?: ProductStock
}

const isFilterOpen = ref(false)
const activeFilterSection = ref('style')

const filterSections = [
  {
    id: 'categories',
    label: 'Categories',
    options: ['Women', 'Men', 'Kids', 'Accessories'],
  },
  {
    id: 'price',
    label: 'Price',
    options: ['$0 - $500', '$500 - $1,500', '$1,500 - $3,000', '$3,000+'],
  },
  {
    id: 'color',
    label: 'Color',
    options: ['Black', 'White', 'Navy', 'Camel'],
  },
  {
    id: 'size',
    label: 'Size',
    options: ['XS', 'S', 'M', 'L', 'XL'],
  },
  {
    id: 'textile',
    label: 'Textile',
    options: ['Cotton', 'Wool', 'Silk', 'Knit'],
  },
  {
    id: 'style',
    label: 'Style',
    options: ['Casual', 'Fit & Flare', 'For Holidays'],
  },
  {
    id: 'brand',
    label: 'Brand',
    options: ['Prada', 'Valentino', 'Bottega Veneta', 'Fendi'],
  },
]

function toggleFilterSection(sectionId: string) {
  activeFilterSection.value = activeFilterSection.value === sectionId ? '' : sectionId
}

const products: Product[] = [
  {
    brand: 'Prada',
    name: 'Crossback Halter Dress',
    description: 'A shapely halter dress designed with slinky crossback straps and a leg-baring slit for polished evenings.',
    price: '$2,400.00',
    priceRange: '$2,400.00 - $2,650.00',
    imagePosition: '10% top',
    imageSize: '305% auto',
    imageAlt: 'Model wearing a black crossback halter dress',
    badges: [
      { label: 'Best Seller' },
      { label: '-4%', tone: 'sale' },
    ],
    colors: [
      { name: 'Black', value: '#050505' },
      { name: 'Navy', value: '#17405f' },
      { name: 'Brown', value: '#4a240d' },
    ],
  },
  {
    brand: 'Oscar de la Renta',
    name: 'Metallic Plisse Gown',
    description: 'A softly gleaming gown with sculpted pleats and a formal silhouette for occasion dressing.',
    price: '$4,900.00',
    imagePosition: '36% top',
    imageSize: '305% auto',
    imageAlt: 'Model wearing a metallic pleated gown',
  },
  {
    brand: 'Jacquemus',
    name: 'Ruched Draped Midi Dress',
    description: 'Warm neutral jersey is gathered through the waist for a refined shape with easy movement.',
    price: '$1,250.00',
    imagePosition: '55% top',
    imageSize: '255% auto',
    imageAlt: 'Model wearing a neutral ruched midi dress',
    colors: [
      { name: 'Sand', value: '#c8a37f' },
      { name: 'Ivory', value: '#f4efe5' },
    ],
  },
  {
    brand: 'Valentino',
    name: 'V Logo Pocket Wool & Silk Dress',
    description: 'A clean short-sleeve dress finished with statement pocket details and an easy tailored line.',
    price: '$6,500.00',
    compareAt: '$7,500.00',
    imagePosition: '48% top',
    imageSize: '305% auto',
    imageAlt: 'Model wearing a white short sleeve dress',
    badges: [
      { label: '-13%', tone: 'sale' },
    ],
  },
  {
    brand: 'Bottega Veneta',
    name: 'Sequin Textured Knit A-Line Gown',
    description: 'Shimmering sequins illuminate a textured knit gown in a simply elegant A-line cut.',
    price: '$6,500.00',
    compareAt: '$7,000.00',
    imagePosition: '50% top',
    imageSize: '245% auto',
    imageAlt: 'Model wearing a sequin textured A-line gown',
    badges: [
      { label: '-7%', tone: 'sale' },
    ],
  },
  {
    brand: 'Fendi',
    name: 'Melody Fleece Pullover Sweatshirt',
    description: 'A relaxed pullover with a wide hemline, slouchy turtleneck, and comfort-first fleece texture.',
    price: '$850.00',
    compareAt: '$900.00',
    imagePosition: '100% top',
    imageSize: '300% auto',
    imageAlt: 'Model wearing a dark fleece pullover sweatshirt',
    badges: [
      { label: '-6%', tone: 'sale' },
      { label: 'Featured' },
    ],
  },
  {
    brand: 'Frame',
    name: 'Le Cutoff Denim Shorts',
    description: 'A relaxed fit boosts the laid-back look of these everyday cutoff denim shorts.',
    price: '$100.00',
    compareAt: '$150.00',
    imagePosition: '88% top',
    imageSize: '235% auto',
    imageAlt: 'Model wearing black cutoff denim shorts',
    badges: [
      { label: '-33%', tone: 'sale' },
    ],
    stock: {
      sold: 9,
      available: 11,
    },
  },
  {
    brand: 'The Row',
    name: 'Sleeveless Cotton Column Dress',
    description: 'A minimal column dress cut from smooth cotton with a long, streamlined shape.',
    price: '$1,790.00',
    imagePosition: '8% top',
    imageSize: '320% auto',
    imageAlt: 'Model wearing a sleeveless cotton column dress',
    colors: [
      { name: 'Black', value: '#050505' },
      { name: 'Cream', value: '#e9dfd1' },
    ],
  },
  {
    brand: 'Toteme',
    name: 'Open Knit Halter Dress',
    description: 'Openwork knit texture brings a light seasonal feel to this fitted halter dress.',
    price: '$980.00',
    imagePosition: '77% top',
    imageSize: '290% auto',
    imageAlt: 'Model wearing a white open knit halter dress',
  },
  {
    brand: 'Khaite',
    name: 'Celia Compact Knit Dress',
    description: 'A compact knit dress with clean shaping and a versatile midi length.',
    price: '$1,480.00',
    imagePosition: '60% top',
    imageSize: '275% auto',
    imageAlt: 'Model wearing a compact knit dress',
    badges: [
      { label: 'New' },
    ],
  },
  {
    brand: 'Loewe',
    name: 'Draped Jersey Dress',
    description: 'Fluid jersey is shaped into soft folds for a dress that balances ease with structure.',
    price: '$2,100.00',
    imagePosition: '42% top',
    imageSize: '285% auto',
    imageAlt: 'Model wearing a draped jersey dress',
    colors: [
      { name: 'Camel', value: '#b4865e' },
      { name: 'Black', value: '#070707' },
    ],
  },
  {
    brand: 'Saint Laurent',
    name: 'Tailored Wool Mini Dress',
    description: 'Sharp tailoring and a concise mini length create a polished day-to-night wardrobe piece.',
    price: '$3,300.00',
    compareAt: '$3,800.00',
    imagePosition: '93% top',
    imageSize: '300% auto',
    imageAlt: 'Model wearing a tailored mini dress',
    badges: [
      { label: '-13%', tone: 'sale' },
    ],
  },
]
</script>

<template>
  <main class="bg-white text-black">

    <section class="border-b border-black/15 bg-white" aria-label="Shop controls">
      <div class="flex min-h-[45px] w-full items-center gap-4 px-4 py-3 text-[11px] font-bold uppercase tracking-normal text-gray sm:px-8">
        <p class="shrink-0">Showing 1-24 of 64 results</p>

        <div class="ml-auto flex shrink-0 items-center justify-end gap-6">
          <button class="inline-flex items-center gap-1.5 uppercase transition-colors hover:text-black" type="button">
            Default sorting
            <Icon name="lucide:chevron-down" class="h-2.5 w-2.5" aria-hidden="true" />
          </button>

          <button
            class="inline-flex h-[30px] min-w-[110px] items-center justify-center gap-2 bg-black px-5 text-xs font-black uppercase text-white transition-colors hover:bg-gray"
            type="button"
            @click="isFilterOpen = true"
          >
            <Icon name="lucide:sliders-horizontal" class="h-3.5 w-3.5" aria-hidden="true" />
            Filter
          </button>
        </div>
      </div>
    </section>

    <section class="bg-white" aria-label="Product list">
      <div class="grid sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
        <ProductCard
          v-for="product in products"
          :key="`${product.brand}-${product.name}`"
          :product="product"
        />
      </div>
    </section>

    <Teleport to="body">
      <Transition
        enter-active-class="transition-opacity duration-300 ease-out"
        enter-from-class="opacity-0"
        enter-to-class="opacity-100"
        leave-active-class="transition-opacity duration-200 ease-in"
        leave-from-class="opacity-100"
        leave-to-class="opacity-0"
      >
        <div
          v-if="isFilterOpen"
          class="fixed inset-0 z-50 bg-black/30"
          aria-hidden="true"
          @click="isFilterOpen = false"
        />
      </Transition>

      <Transition
        enter-active-class="transition-transform duration-300 ease-out"
        enter-from-class="-translate-x-full"
        enter-to-class="translate-x-0"
        leave-active-class="transition-transform duration-200 ease-in"
        leave-from-class="translate-x-0"
        leave-to-class="-translate-x-full"
      >
        <aside
          v-if="isFilterOpen"
          class="fixed left-0 top-0 z-50 h-dvh w-[min(335px,calc(100vw-32px))] overflow-y-auto border-r border-black bg-white px-[30px] py-5 text-black shadow-2xl sm:w-[360px]"
          role="dialog"
          aria-modal="true"
          aria-label="Product filters"
        >
          <button
            class="ml-auto flex h-6 w-6 items-center justify-center text-black transition-colors hover:text-gray"
            type="button"
            aria-label="Close filters"
            @click="isFilterOpen = false"
          >
            <Icon name="lucide:x" class="h-5 w-5" aria-hidden="true" />
          </button>

          <div class="mt-7">
            <section
              v-for="section in filterSections"
              :key="section.id"
              class="border-b border-black/15"
            >
              <button
                class="flex w-full items-center justify-between py-[17px] text-left text-[15px] font-extrabold uppercase tracking-normal"
                type="button"
                :aria-expanded="activeFilterSection === section.id"
                @click="toggleFilterSection(section.id)"
              >
                {{ section.label }}
                <Icon
                  :name="activeFilterSection === section.id ? 'lucide:minus' : 'lucide:plus'"
                  class="h-4 w-4"
                  aria-hidden="true"
                />
              </button>

              <div
                class="grid transition-[grid-template-rows,opacity] duration-300 ease-out"
                :class="activeFilterSection === section.id ? 'grid-rows-[1fr] opacity-100' : 'grid-rows-[0fr] opacity-0'"
              >
                <div class="overflow-hidden">
                  <ul class="space-y-3 pb-5">
                    <li
                      v-for="option in section.options"
                      :key="option"
                    >
                      <label class="flex cursor-pointer items-center gap-3 text-sm font-medium">
                        <input
                          class="h-2.5 w-2.5 appearance-none border border-black/15 bg-white checked:border-black checked:bg-black"
                          type="checkbox"
                        >
                        <span>{{ option }} <span class="text-[11px] text-gray">1</span></span>
                      </label>
                    </li>
                  </ul>
                </div>
              </div>
            </section>
          </div>
        </aside>
      </Transition>
    </Teleport>
  </main>

  <AppFooter />
</template>
