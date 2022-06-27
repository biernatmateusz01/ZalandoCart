<template>
  <div
    class="flex flex-col justify-between px-1.5 w-full md:w-1/2 lg:w-1/3 xl:w-1/4 group pt-6 pb-3 cursor-pointer"
  >
    <div class="relative inline-block h-full">
      <img 
        class="object-cover w-full h-full transition-opacity duration-300 ease-in opacity-100 "
        :class="product.hasOwnProperty('secondPhoto') && product.secondPhoto && 'group-hover:opacity-0'"
        :src="product.photo"
        alt="product-img"
      />
      <img v-if="product.hasOwnProperty('secondPhoto') && product.secondPhoto"
        class="absolute top-0 left-0 z-40 object-cover w-full h-full transition-opacity duration-300 ease-in opacity-0 group-hover:opacity-100"
        :src="product.secondPhoto"
        alt="product-img"
      />
      <button
        @click="$emit('addItem')"
        class="absolute right-0 z-50 flex items-center justify-center w-10 h-10 bg-white top-2"
      >
        <BaseIcon><img class="h-[80%] w-[80%] block m-auto" src="https://cdn3.iconfinder.com/data/icons/e-commerce-2-1/256/2-512.png" alt=""></BaseIcon>
      </button>
      <BaseSale v-if="product.hasOwnProperty('sale')" :sale="product.sale" />
      <BaseDiscount
        v-if="product.hasOwnProperty('discountCode')"
        :discountCode="product.discountCode"
      />
    </div>
    <div class="h-[124px]">
      <ProductName :brand="product.brand" :productName="product.productName" />
      <BasePrice :price="product.price" />
    </div>
  </div>
</template>

<script>
import BaseIcon from "./BaseIcon.vue";
import BasePrice from "./BasePrice.vue";
import ProductName from "./ProductName.vue";
import BaseSale from "./BaseSale.vue";
import BaseDiscount from "./BaseDiscount.vue";

export default {
  props: {
    product: Object,
  },
  emits: {
    addItem: null,
  },
  components: {
    BaseIcon,
    BasePrice,
    ProductName,
    BaseSale,
    BaseDiscount,
  },
};
</script>
