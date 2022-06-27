<template>
  <div class="flex flex-col p-4">
    <div class="relative inline-block w-40 h-48">
      <img
        class="object-cover w-full h-full transition-opacity duration-300 ease-in opacity-100 group-hover:opacity-0"
        :src="product.photo"
        alt="product-img"
      />
    </div>
    <div class="w-40">
      <ProductName :brand="product.brand" :productName="product.productName" />
      <BasePrice :price="product.price" />
    </div>
  </div>
</template>

<script>
import BasePrice from "../components/BasePrice.vue";
import ProductName from "../components/ProductName.vue";
export default {
  props: {
    product: Object,
  },
  emits: {
    addItem: null,
  },
  components: {
    BasePrice,
    ProductName,
  },
  methods: {
    removeItem() {},
  },
};
</script>
