<template>
  <q-card>
    <q-card-section class="reserve-text">
      <span>Your cart is reserved for 10:00 minutes</span>
    </q-card-section>
    <q-card-section class="express" v-if="paymentMethods.length">
      <span>Express Checkout</span>
      <div>
        <q-btn v-for="item in paymentMethods" :key="item.name">
          {{ item.name }}
        </q-btn>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent } from "vue";

const paymentMethods = [
  {
    name: "ShopPay",
    icon: "1",
  },
  {
    name: "PayPal",
    icon: "2",
  },
  {
    name: "GPay",
    icon: "3",
  },
];

export default defineComponent({
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
    padding: 30px !important;
    background-color: #ebecf3;
    border-radius: 16px;
    > span {
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
      font-size: 20px;
    }
    > div {
      display: flex;
      gap: 20px;
      button {
        max-width: 150px;
        max-height: 50px;
      }
      > :first-child {
        background-color: rgba(90, 49, 244, 0.1);
        border: 1px solid rgba(90, 49, 244, 0.6);
        border-radius: 16px;
      }
      > :nth-child(2) {
        background-color: rgba(17, 57, 132, 0.1);
        border: 1px solid rgba(17, 57, 132, 0.6);
        border-radius: 16px;
      }
      > :last-child {
        background-color: rgba(234, 64, 50, 0.1);
        border: 1px solid rgba(234, 64, 50, 0.6);
        border-radius: 16px;
      }
    }
  }
}
</style>
