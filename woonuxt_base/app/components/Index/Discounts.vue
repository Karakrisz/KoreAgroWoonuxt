<script setup lang="ts">
// Use better composables for data fetching
const {
  data: saleProductsData,
  pending,
  error,
} = useLazyAsyncData(
  'sale-products',
  () =>
    useAsyncGql('getProducts', {
      first: 4,
      orderby: 'POPULARITY',
      where: {
        onSale: true,
      },
    }).then(({ data }) => data.value?.products?.nodes || []),
  {
    default: () => [],
    immediate: true,
    watch: false,
  },
);

watchEffect(() => {
  if (error.value) {
    console.error('Error fetching products:', error.value);
  }
});

const onSaleProducts = computed(() => saleProductsData.value);
</script>

<template>
  <section class="w-full py-[50px]">
    <div class="container">
      <!-- <h2 class="pb-10">AKTUÁLIS AKCIÓINK</h2> -->

      <TransitionGroup v-if="pending" name="fade" tag="div"
        class="grid grid-cols-1 md:grid-cols-2 xl:grid-cols-3 gap-[24px] pb-[35px]">
        <div v-for="i in 3" :key="i" class="animate-pulse">
          <div class="bg-stone-200 h-48 rounded-lg mb-4" />
          <div class="space-y-3">
            <div class="h-4 bg-stone-200 rounded w-3/4" />
            <div class="h-4 bg-stone-200 rounded w-1/2" />
            <div class="h-4 bg-stone-200 rounded w-1/4" />
          </div>
        </div>
      </TransitionGroup>

      <template v-else>
        <div v-if="error" class="text-center text-red-600 pb-[35px]">Failed to load products. Please try again later.
        </div>
        <ProductRow v-else :products="onSaleProducts"
          class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6" />
      </template>

      <div class="flex gap-[10px] items-center justify-center mt-10">
        <NuxtLink to="/products"
          class="px-6 py-3 font-medium text-white transition-colors bg-gray-900 rounded-full hover:bg-gray-800"> Több
          termék
          betöltése
        </NuxtLink>
      </div>
    </div>
  </section>
</template>
