<template>
  <aside class="flex column q-gutter-md col col-lg-4">
    <checkout-subtotal class="hiddenOnSM" />
    <div class="order-information">
      <div>
        <q-icon name="lock"></q-icon>
        <span class="information-text">
          Secure SSL Encryption & Guaranteed Safe Checkout
        </span>
      </div>
      <checkout-payment-networks />
    </div>
    <checkout-features class="hiddenOnSM" />
    <checkout-payment-form @triggerSubmit="passSubmitToParent" />
  </aside>
</template>

<script>
import { defineComponent } from "vue";

import CheckoutSubtotal from "./CheckoutSubtotal.vue";
import CheckoutPaymentNetworks from "./CheckoutPaymentNetworks.vue";
import CheckoutFeatures from "./CheckoutFeatures.vue";
import CheckoutPaymentForm from "./CheckoutPaymentForm.vue";

export default defineComponent({
  components: {
    CheckoutSubtotal,
    CheckoutPaymentNetworks,
    CheckoutFeatures,
    CheckoutPaymentForm,
  },
  name: "CheckoutAsideContent",
  emits: ["triggerSubmit"],
  setup(props, { emit }) {
    const passSubmitToParent = () => {
      console.log("passed");
      emit("triggerSubmit");
    };
    return {
      passSubmitToParent,
    };
  },
});
</script>

<style scoped lang="scss">
aside {
  @media (max-width: 900px) {
    margin: 0;
    align-self: center;
    max-width: 750px !important;
    flex-direction: column-reverse;
    .hiddenOnSM {
      display: none;
    }
    > div {
      margin-left: 0;
    }
  }
}
.order-information {
  padding: 40px 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
  background: #ffffff;
  border-radius: 16px;

  .thank-you-text {
    font-family: "Poppins";
    font-style: normal;
    font-weight: 600;
    font-size: 24px;
    line-height: 34px;
    text-align: center;
    color: #000034;
  }
  .order-confirmed-text {
    font-family: "Poppins";
    font-style: normal;
    font-weight: 500;
    font-size: 16px;
    line-height: 26px;
    text-align: center;
    color: #4b4e68;
  }
  .q-card {
    border: none;
    box-shadow: none;
    background: #ffffff;
  }
}
</style>
