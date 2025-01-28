<script setup lang="ts">
import { ref, onMounted, onUnmounted, watch } from 'vue';

const links = [
  { name: 'Főoldal', href: '/' },
  { name: 'Rólunk', href: 'rolunk' },
  { name: 'Referenciák', href: 'referenciak' },
  { name: 'Új gépek', href: 'uj-gepek' },
  { name: 'Használt gépek', href: 'hasznalt-gepek' },
  { name: 'Kapcsolat', href: 'kapcsolat' },
];

const isMobileMenuOpen = ref(false);
const isScrolled = ref(false);

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const checkScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

const disableScroll = () => {
  document.body.style.overflow = 'hidden';
};

const enableScroll = () => {
  document.body.style.overflow = '';
};

watch(isMobileMenuOpen, (newValue) => {
  if (newValue) {
    disableScroll();
  } else {
    enableScroll();
  }
});

onMounted(() => {
  window.addEventListener('scroll', checkScroll);
});

onUnmounted(() => {
  window.removeEventListener('scroll', checkScroll);
  enableScroll(); // Ensure scroll is re-enabled when component is unmounted
});
</script>

<template>
  <!-- <ProductSearch class="hidden md:inline-flex max-w-[320px]" /> -->
  <!-- <SignInLink />
        <CartTrigger /> -->

  <header class="sticky top-0 z-50 transition-shadow duration-300">
    <div
      class="items-center justify-center hidden w-full h-8 gap-4 px-4 text-xs transition-all duration-300 md:flex bg-Grey md:text-sm"
      :class="{ 'h-0 overflow-hidden': isScrolled }">
      <MenuTrigger class="lg:hidden" />
      <p class="hidden md:block"><span class="font-semibold">Nyitvatartás: </span>Hétfő - Pétek: 7:30 - 16:00</p>
      <div class="hidden md:block h-3.5 w-[1px] bg-Grey-2"></div>
      <p class="font-semibold">+36 70 775 56 66</p>
    </div>

    <div class="relative w-full bg-Light shadow-Shadow md:shadow-none">
      <div class="container flex items-center justify-between gap-4 px-4 py-4 md:py-7 md:gap-9 md:px-0">
        <NuxtLink to="/" class="flex-shrink-0 transition-transform duration-300 hover:scale-105">
          <NuxtImg src="/img/logo.svg" class="w-[150px] md:w-[202px] pb-1"></NuxtImg>
        </NuxtLink>
        <div class="relative flex-1 hidden md:block">
          <input
            class="w-full pl-6 transition-all duration-300 border-0 pr-14 placeholder:text-Grey-2 bg-light rounded-rounded-7 shadow-Shadow focus:ring-Primary focus:shadow-lg"
            placeholder="Keressen a termékek között..." />
          <PhosphorIconMagnifyingGlass class="absolute translate-y-1/2 top-1 right-6" />
        </div>
        <NuxtLink
          class="hidden px-4 py-2 transition-all duration-300 rounded-full md:block bg-Primary button text-Light hover:bg-opacity-90 hover:shadow-md">
          Kérjen árajánlatot
        </NuxtLink>
        <button @click="toggleMobileMenu"
          class="p-2 transition-colors duration-300 rounded-full md:hidden text-Primary hover:bg-Grey">
        </button>
      </div>
    </div>

    <div class="relative z-10 hidden w-screen md:block">
      <nav class="relative z-10 container bg-Light w-fit px-[50px] rounded-full shadow-Shadow_Strong">
        <div class="flex items-center justify-center text-center">
          <NuxtLink v-for="(link, index) in links" :key="index" :to="link.href"
            class="px-[18.5px] py-3 text-sm font-medium hover:bg-Grey transition-all duration-300 relative group"
            activeClass="bg-Primary text-Light hover:bg-Primary hover:text-white">
            {{ link.name }}
            <span
              class="absolute bottom-0 left-0 w-full h-0.5 bg-Primary transform scale-x-0 transition-transform duration-300 group-hover:scale-x-100"></span>
          </NuxtLink>
        </div>
      </nav>
      <div :class="{ 'shadow-sm': isScrolled }" class="absolute top-0 bottom-0 z-0 w-full bg-Light h-1/2"></div>
    </div>
  </header>
</template>

<style scoped>
.sticky {
  transition: transform 0.3s ease-in-out;
}

.sticky.shadow-md {
  transform: translateY(-32px);
}
</style>
