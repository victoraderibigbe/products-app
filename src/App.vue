<template>
  <div v-if="products.length > 0">
    <HeaderComponent />
    <div class="flex flex-wrap items-center gap-3 p-5 justify-evenly">
      <ProductsCard :products="products" />
    </div>
  </div>
  <div v-else class="flex items-center justify-center w-full h-screen">
    <LoadingComponent />
  </div>
</template>

<script setup>
import { useProductStore } from '@/stores/productStore'
import { storeToRefs } from 'pinia'
import { onMounted, ref } from 'vue'
import ProductsCard from '@/components/ProductsCard.vue'
import HeaderComponent from '@/components/HeaderComponent.vue'
import LoadingComponent from '@/components/LoadingComponent.vue'

const store = useProductStore()
const { products } = storeToRefs(store)

onMounted(() => {
  store.fetchProducts()
})
</script>

<style></style>
