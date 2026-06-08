<script setup lang="ts">
const navItems = [
  { label: 'Homes', href: '/', hasMenu: true },
  { label: 'Shop', href: '/shop', hasMenu: true },
  { label: 'Blog', href: '/blog', hasMenu: true },
  { label: 'Pages', href: '/pages', hasMenu: true },
  { label: 'Mega', href: '/mega', hasMenu: true },
  { label: 'Contacts', href: '/contacts', hasMenu: false },
]
</script>

<template>
  <header class="w-full bg-white text-black">
    <div class="relative flex h-[67px] items-center border-b border-black px-4 sm:px-8">
      <p class="hidden text-[11px] font-bold uppercase tracking-0 sm:block">
        Best special offers! 40% off!
      </p>

      <NuxtLink
        to="/"
        aria-label="Moderno home"
        class="absolute left-1/2 -translate-x-1/2 text-[26px] font-black uppercase leading-none tracking-[0.42em]"
      >
        Moderno
      </NuxtLink>

      <div class="ml-auto flex items-center gap-4">
        <button class="header-icon" type="button" aria-label="Account">
          <Icon name="lucide:user" class="h-[18px] w-[18px]" aria-hidden="true" />
        </button>

        <button class="header-icon" type="button" aria-label="Search">
          <Icon name="lucide:search" class="h-[18px] w-[18px]" aria-hidden="true" />
        </button>

        <button class="header-icon" type="button" aria-label="Wishlist">
          <Icon name="lucide:heart" class="h-[18px] w-[18px]" aria-hidden="true" />
        </button>

        <button class="header-icon" type="button" aria-label="Shopping bag">
          <Icon name="lucide:shopping-bag" class="h-[18px] w-[18px]" aria-hidden="true" />
        </button>
      </div>
    </div>

    <nav class="hidden h-11 items-center justify-center border-b border-white md:flex" aria-label="Main navigation">
      <ul class="flex items-center gap-9">
        <li v-for="item in navItems" :key="item.label">
          <NuxtLink
            :to="item.href"
            class="group inline-flex items-center gap-1.5 text-xs font-semibold uppercase leading-none text-black transition-colors hover:text-gray"
          >
            {{ item.label }}
            <Icon
              v-if="item.hasMenu"
              name="lucide:chevron-down"
              class="h-2.5 w-2.5 transition-transform group-hover:translate-y-0.5"
              aria-hidden="true"
            />
          </NuxtLink>
        </li>
      </ul>
    </nav>

    <nav class="border-b border-white px-4 py-3 md:hidden" aria-label="Mobile navigation">
      <ul class="flex items-center gap-5 overflow-x-auto">
        <li v-for="item in navItems" :key="`mobile-${item.label}`" class="shrink-0">
          <NuxtLink :to="item.href" class="text-xs font-semibold uppercase text-black">
            {{ item.label }}
          </NuxtLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
.header-icon {
  display: inline-flex;
  width: 18px;
  height: 18px;
  align-items: center;
  justify-content: center;
  color: var(--color-black);
}

.tracking-0 {
  letter-spacing: 0;
}
</style>
