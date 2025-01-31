<script setup>
import { ref, watch } from 'vue'

const { getSearchQuery, setSearchQuery, clearSearchQuery } = useSearching()
const searchQuery = ref(getSearchQuery())

const reset = () => {
  clearSearchQuery()
  searchQuery.value = ''
}

watch(getSearchQuery, (value) => {
  if (!value) reset()
})

const handleSubmit = () => {
  setSearchQuery(searchQuery.value)
}
</script>

<template>
  <form class="relative items-center rounded-md" @submit.prevent="handleSubmit">
    <input v-model="searchQuery" type="text" :placeholder="$t('messages.shop.searchProducts')"
      class="w-full pl-6 transition-all duration-300 border-0 pr-14 placeholder:text-Grey-2 bg-light rounded-rounded-7 shadow-Shadow focus:ring-Primary focus:shadow-lg"
      placeholder="Keressen a termékek között...">
    <span v-if="searchQuery"
      class="absolute z-10 top-1/2 -translate-y-1/2 pt-1 right-12 text-xs rounded cursor-pointer text-gray-600 hover:text-gray-900 transition"
      @click="reset">
      <Icon name="ion:close-outline" size="18" />
    </span>
    <button type="submit"
      class="absolute z-10 right-1  px-1.5 pt-1 top-1/2 -translate-y-1/2 transform transition cursor-not-allowed"
      :class="{ 'bg-primary/20 rounded-md hover:bg-primary/30 !cursor-pointer': searchQuery?.length >= 2 }">
      <Icon name="ph:magnifying-glass" size="20"
        :class="searchQuery?.length >= 2 ? 'text-primary-dark' : 'text-disabled '" />
    </button>
  </form>
</template>