<template>
  <aside class="flex column q-gutter-md col col-lg-4">
    <checkout-subtotal />
    <checkout-payment-networks />
    <checkout-features />
    <checkout-payment-form />
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
  setup() {
    return {};
  },
});
</script>
