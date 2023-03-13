<template>
  <q-card>
    <q-card-section class="flex column">
      <span class="heading">Checkout</span>
      <span class="attention"
        >Strong demand! Complete your order before it's too late!</span
      >
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "CheckoutHeadline",
});
</script>

<style lang="scss" scoped>
.q-card {
  box-shadow: none;
  .heading {
    font-size: 36px;
    font-weight: 700;
    padding: 0;
    margin-bottom: 50px;
  }
  .attention {
    font-size: 20px;
    font-weight: 400;
    color: #4b4e68;
  }
}
</style>
