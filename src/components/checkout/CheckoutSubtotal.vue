<template>
  <q-card>
    <q-card-section class="flex column productsInfoSection">
      <article
        v-for="item in products"
        :key="item.id"
        class="flex justify-stretch"
      >
        <img :src="item.src" :alt="item.name" />
        <span>{{ item.name }}</span>
        <span>${{ item.price }}</span>
      </article>
      <span class="underline"></span>
    </q-card-section>
    <q-card-section class="totalPrice flex column productsInfoSection">
      <span>Subtotal: ${{ totalPrice }}</span>
      <span>Shipping: Free</span>
      <span class="underline"></span>
      <span>Total ${{ totalPrice }}</span>
    </q-card-section>
  </q-card>
</template>

<script>
import { computed, defineComponent } from "vue";

import nike1 from "../../assets/Nike1.svg";
import nike3 from "../../assets/Nike3.svg";

const products = [
  {
    id: 0,
    name: "Nike sneakers",
    price: 120.9,
    src: nike1,
  },
  {
    id: 2,
    name: "Nike sneakers",
    price: 120.9,
    src: nike3,
  },
];

export default defineComponent({
  name: "CheckoutSubtotal",
  setup() {
    const totalPrice = computed(() =>
      products.reduce((acc, aggr) => (acc += aggr.price), 0).toFixed(2)
    );
    return {
      products,
      totalPrice,
    };
  },
});
</script>
