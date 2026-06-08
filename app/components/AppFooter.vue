<script setup lang="ts">
const footerLinks = [
  'Shop',
  'FAQ',
  'Shipping',
  'Returns',
  'Careers',
  'Terms & Conditions',
  'Privacy Policy',
]

const paymentMethods = ['AMEX', 'Pay', 'G Pay', 'MC', 'Mastercard', 'P', 'OPay', 'VISA']

const socialLinks = [
  {
    label: 'Facebook',
    icon: 'f',
  },
  {
    label: 'Instagram',
    icon: 'ig',
  },
  {
    label: 'X',
    icon: 'X',
  },
  {
    label: 'YouTube',
    icon: 'yt',
  },
]
</script>

<template>
  <footer class="site-footer bg-black px-5 py-16 text-white sm:px-8 lg:px-[70px]">
    <div class="grid gap-14 lg:grid-cols-[1.2fr_0.85fr_1.55fr] lg:gap-20">
      <section aria-labelledby="footer-newsletter-title">
        <h2 id="footer-newsletter-title" class="max-w-[430px] text-[15px] font-black uppercase leading-[1.3] tracking-0">
          Sign up to get 10% off your first order and stay up to date on the latest product releases, special offers and news
        </h2>

        <form class="mt-7 max-w-[380px]" aria-label="Newsletter signup">
          <label class="sr-only" for="footer-email">Your Email</label>
          <input
            id="footer-email"
            class="h-10 w-full border border-white/20 bg-transparent px-4 text-sm font-bold text-white outline-none transition-colors placeholder:text-white/45 focus:border-white"
            type="email"
            placeholder="Your Email *"
          >

          <button
            class="mt-3 inline-flex h-[38px] min-w-[123px] items-center justify-center bg-white/25 px-6 text-xs font-black uppercase tracking-0 text-white transition-colors hover:bg-white hover:text-black"
            type="submit"
          >
            Subscribe
          </button>
        </form>
      </section>

      <nav aria-label="Footer navigation">
        <ul class="space-y-[18px]">
          <li v-for="link in footerLinks" :key="link">
            <NuxtLink class="footer-link text-sm font-black uppercase tracking-0 text-white" to="/shop">
              {{ link }}
            </NuxtLink>
          </li>
        </ul>
      </nav>

      <section class="lg:pl-8" aria-labelledby="footer-contact-title">
        <h2 id="footer-contact-title" class="sr-only">
          Contact information
        </h2>

        <p class="max-w-[430px] text-sm font-bold leading-8 text-white/30">
          If you have any questions regarding your order, products
          or our service, please contact our customer service.
        </p>

        <dl class="mt-6 space-y-4 text-sm uppercase tracking-0">
          <div>
            <dt class="font-black text-white">
              Monday - Friday: 10:00-6:00 PM
            </dt>
          </div>

          <div class="flex flex-wrap gap-x-2 gap-y-1">
            <dt class="font-black text-white/35">
              Phone:
            </dt>
            <dd class="font-black text-white">
              +1 712-339-9294
            </dd>
          </div>

          <div class="flex flex-wrap gap-x-2 gap-y-1">
            <dt class="font-black text-white/35">
              Email:
            </dt>
            <dd class="font-black text-white">
              info@moderno-theme.com
            </dd>
          </div>

          <div class="flex flex-wrap gap-x-2 gap-y-1">
            <dt class="font-black text-white/35">
              Address:
            </dt>
            <dd class="font-black text-white">
              283 N. Glenwood Street, Levittown, NY
            </dd>
          </div>
        </dl>
      </section>
    </div>

    <div class="mt-16 grid items-end gap-10 lg:mt-14 lg:grid-cols-[1.2fr_0.85fr_1.55fr] lg:gap-20">
      <ul class="flex flex-wrap items-center gap-1.5" aria-label="Accepted payment methods">
        <li
          v-for="method in paymentMethods"
          :key="method"
          class="payment-badge flex h-[21px] min-w-[34px] items-center justify-center rounded-[2px] px-1.5 text-[10px] font-black leading-none text-black"
        >
          {{ method }}
        </li>
      </ul>

      <p class="text-sm font-bold text-white/30">
        &copy; 2023 Moderno Theme. All Rights Reserved.
      </p>

      <ul class="flex items-center lg:pl-8" aria-label="Social links">
        <li v-for="social in socialLinks" :key="social.label">
          <NuxtLink
            class="social-link flex h-[57px] w-[54px] items-center justify-center border border-white/10 text-base font-black text-white transition-colors hover:border-white hover:bg-white hover:text-black"
            to="/"
            :aria-label="social.label"
          >
            {{ social.icon }}
          </NuxtLink>
        </li>
      </ul>
    </div>
  </footer>
</template>

<style scoped>
.tracking-0 {
  letter-spacing: 0;
}

.site-footer {
  min-height: 455px;
}

.footer-link {
  transition: color 160ms ease;
}

.footer-link:hover {
  color: var(--color-gray);
}

.payment-badge:nth-child(1) {
  background: #2472b9;
  color: #eaf3ff;
}

.payment-badge:nth-child(2),
.payment-badge:nth-child(3),
.payment-badge:nth-child(6),
.payment-badge:nth-child(8) {
  background: #d8dce1;
}

.payment-badge:nth-child(4) {
  background: #ccd1d7;
}

.payment-badge:nth-child(4)::before,
.payment-badge:nth-child(5)::before {
  width: 14px;
  height: 14px;
  content: "";
  background: #e4262f;
  border-radius: 999px;
}

.payment-badge:nth-child(4)::after,
.payment-badge:nth-child(5)::after {
  width: 14px;
  height: 14px;
  margin-left: -5px;
  content: "";
  background: #e7a624;
  border-radius: 999px;
}

.payment-badge:nth-child(4),
.payment-badge:nth-child(5) {
  gap: 0;
  font-size: 0;
}

.payment-badge:nth-child(5) {
  background: #d3d8de;
}

.payment-badge:nth-child(6) {
  color: #123d7a;
}

.payment-badge:nth-child(7) {
  background: #5944b7;
  color: #d8ccff;
}

@media (max-width: 1023px) {
  .site-footer {
    min-height: auto;
  }
}

</style>
