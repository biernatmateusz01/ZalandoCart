<template>
  <div>
    <Transition name="v">
      <div
        v-if="isCartOpen"
        class="fixed top-0 left-0 z-[9999] flex flex-col items-center w-3/4 h-screen overflow-auto bg-white border-r-4 border-orange-600"
      >
        <div class="absolute top-5 right-5">
          <div
            class="z-[90] flex items-center justify-center w-12 h-12 border-2 border-orange-600 rounded-full"
          >
            <button
              v-on:click="removeCart()"
              class="z-[90] flex items-center justify-center w-full h-full"
            >
              <BaseIcon class="text-orange-600"><img src="https://cdn2.iconfinder.com/data/icons/weby-flat-vol-1/512/1_multiplication-multiply-close-remove-orange-512.png" alt=""></BaseIcon>
            </button>
          </div>
        </div>

        <span class="pt-4 mt-8 font-semibold text-black">Twój koszyk :</span>

        <div class="flex flex-wrap items-center justify-center w-full">
          <SmallItem
            v-for="product in yourProducts"
            :key="product.id"
            :product="product"
          />
        </div>

        <span class="my-4">Do zapłaty : {{ totalPrice }} zł</span>
      </div>
    </Transition>
    <div
      class="fixed z-50 flex items-center justify-center w-12 h-12 border-2 border-orange-600 rounded-full top-5 left-5"
    >
      <button
        v-on:click="openCart()"
        class="flex items-center justify-center w-full h-full"
      >
        <BaseIcon class="text-orange-600 ">
          <img class="w-[90%] h-[90%] block m-auto" src="https://cdn0.iconfinder.com/data/icons/flat-round-arrow-arrow-head/512/Red_Arrow_Right-2-1024.png" alt="">
        </BaseIcon>
      </button>
    </div>
  </div>
</template>

<script>
import BaseIcon from "../components/BaseIcon.vue";
import SmallItem from "../components/SmallItem.vue";

export default {
  props: {
    yourProducts: Array,
  },

  components: {
    BaseIcon,
    SmallItem,
  },

  computed: {
    totalPrice() {
      let price = 0;
      this.yourProducts.forEach((item) => {
        price += +item.price;
      });
      return price.toFixed(2);
    },
  },

  data() {
    return {
      isCartOpen: false,
    };
  },

  methods: {
    removeCart() {
      this.isCartOpen = false;
    },
    openCart() {
      this.isCartOpen = true;
    },
    amountToPay() {},
  },
};
</script>

<style>
.v-enter-from,
.v-leave-to {
  transform: translateX(-100%);
}
.v-enter-active,
.v-leave-active {
  transition: transform 1s linear;
}
</style>
