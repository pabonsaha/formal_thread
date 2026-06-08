<script setup lang="ts">
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

const props = defineProps<{
  product: Product
}>()

const stockTotal = computed(() => {
  if (!props.product.stock) {
    return 0
  }

  return props.product.stock.sold + props.product.stock.available
})

const stockPercent = computed(() => {
  if (!props.product.stock || stockTotal.value === 0) {
    return 0
  }

  return Math.round((props.product.stock.sold / stockTotal.value) * 100)
})
</script>

<template>
  <article class="product-card">
    <div
      class="product-image"
      :style="{
        backgroundPosition: product.imagePosition,
        backgroundSize: product.imageSize ?? '310% auto',
      }"
      role="img"
      :aria-label="product.imageAlt"
    >
      <div v-if="product.badges?.length" class="absolute right-3 top-3 flex items-start gap-1.5">
        <span
          v-for="badge in product.badges"
          :key="badge.label"
          class="badge"
          :class="badge.tone === 'sale' ? 'badge-sale' : 'badge-dark'"
        >
          {{ badge.label }}
        </span>
      </div>
    </div>

    <div class="flex min-h-[250px] flex-col px-5 pb-7 pt-4 sm:px-6">
      <div v-if="product.colors?.length" class="mb-4 flex items-center gap-1.5" aria-label="Available colors">
        <span
          v-for="color in product.colors"
          :key="color.name"
          class="h-4 w-4 rounded-full border border-black/10"
          :style="{ backgroundColor: color.value }"
          :aria-label="color.name"
        />
      </div>

      <p class="text-[11px] font-bold uppercase leading-none tracking-0">
        {{ product.brand }}
      </p>

      <h3 class="mt-4 text-base font-semibold leading-snug tracking-0">
        {{ product.name }}
      </h3>

      <p class="mt-4 text-sm leading-6 text-gray">
        {{ product.description }}
      </p>

      <div class="mt-5 text-sm font-semibold leading-none tracking-0">
        <span v-if="product.priceRange">{{ product.priceRange }}</span>
        <span v-else>{{ product.price }}</span>
        <span v-if="product.compareAt" class="ml-2 text-xs text-gray line-through">
          {{ product.compareAt }}
        </span>
      </div>

      <div v-if="product.stock" class="mt-auto pt-6">
        <div class="h-1 bg-black/10">
          <div class="h-full bg-[#ff5a4f]" :style="{ width: `${stockPercent}%` }" />
        </div>

        <div class="mt-4 flex items-center gap-7 text-[11px] font-bold uppercase tracking-0 text-gray">
          <span>Sold: <strong class="text-black">{{ product.stock.sold }}</strong></span>
          <span>Available: <strong class="text-black">{{ product.stock.available }}</strong></span>
        </div>
      </div>
    </div>
  </article>
</template>

<style scoped>
.tracking-0 {
  letter-spacing: 0;
}

.product-card {
  display: flex;
  min-width: 0;
  flex-direction: column;
  border-left: 1px solid rgba(7, 7, 7, 0.16);
  background: var(--color-white);
}

.product-card:last-child {
  border-right: 1px solid rgba(7, 7, 7, 0.16);
}

.product-image {
  position: relative;
  min-height: 470px;
  background-color: #fff;
  background-image: url('/spring-collection-reference.png');
  background-repeat: no-repeat;
}

.badge {
  display: inline-flex;
  min-height: 25px;
  align-items: center;
  border: 1px solid currentColor;
  padding: 0 9px;
  font-size: 11px;
  font-weight: 700;
  line-height: 1;
  text-transform: uppercase;
}

.badge-dark {
  color: var(--color-black);
}

.badge-sale {
  color: #ff463a;
}

@media (max-width: 1279px) {
  .product-card:nth-child(4n) {
    border-right: 1px solid rgba(7, 7, 7, 0.16);
  }
}

@media (max-width: 1023px) {
  .product-card:nth-child(3n) {
    border-right: 1px solid rgba(7, 7, 7, 0.16);
  }

  .product-image {
    min-height: 430px;
  }
}

@media (max-width: 767px) {
  .product-card {
    border-right: 1px solid rgba(7, 7, 7, 0.16);
  }

  .product-image {
    min-height: 390px;
    background-size: 220% auto !important;
  }
}
</style>
