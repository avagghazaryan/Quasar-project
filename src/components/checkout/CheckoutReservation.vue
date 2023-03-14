<template>
  <q-card class="flex column q-gutter-md">
    <q-card-section class="reserve-text">
      <span>Your cart is reserved for 10:00 minutes</span>
    </q-card-section>
    <q-card-section class="express" v-if="paymentMethods.length">
      <span>Express Checkout</span>
      <div>
        <img
          v-for="item in paymentMethods"
          :key="item.name"
          :src="item.src"
          alt=""
        />
      </div>
    </q-card-section>
    <checkout-warranty />
  </q-card>
</template>

<script>
import { defineComponent } from "vue";
import "@fontsource/poppins";
import shopPay from "../../assets/shopPay.svg";
import payPal from "../../assets/paypal2.svg";
import gPay from "../../assets/gpay.svg";
import CheckoutWarranty from "./CheckoutWarranty.vue";

const paymentMethods = [
  {
    id: "1",
    name: "ShopPay",
    src: shopPay,
  },
  {
    id: "2",
    name: "PayPal",
    src: payPal,
  },
  {
    id: "3",
    name: "GPay",
    src: gPay,
  },
];

export default defineComponent({
  components: { CheckoutWarranty },
  name: "CheckoutReservation",
  setup() {
    return {
      paymentMethods,
    };
  },
});
</script>

<style lang="scss" scoped>
.q-card {
  box-shadow: none;
  > .reserve-text {
    padding: 15px 30px;
    background-color: #ebecf3;
    border-radius: 16px;
    > span {
      font-family: Poppins;
      font-size: 16px;
    }
  }
  .express {
    padding: 30px !important;
    display: flex;
    flex-flow: column wrap;
    gap: 20px;
    background-color: #ffffff;
    border: 1px solid #d6d8ee;
    border-radius: 16px;
    > span {
      font-family: Poppins;
      font-weight: 600;
      font-size: 20px;
    }
    > div {
      display: flex;
      gap: 20px;
      img {
        width: 115px;
      }
    }
  }
}
</style>
