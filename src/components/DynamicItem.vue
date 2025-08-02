<template>
 <div v-for="(product, index) in products" :key="index">
  <p>{{ product.title }}</p>
  {{ product }}
  <img :src="product.image" alt="" />
 </div>
</template>

<script setup>
import {ref, onMounted} from 'vue'

const products = ref([])

onMounted(async () => {
  try {
    const response = await fetch('https://fakestoreapi.com/products')
    const data = await response.json()
    products.value = data.slice(0, 9)
  } catch (err) {
    console.error('Hata:', err)
  }
})
</script>