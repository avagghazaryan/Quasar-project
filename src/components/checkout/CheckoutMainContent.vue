<template>
  <main class="flex column q-gutter-md col col-lg-4">
    <checkout-headline />
    <checkout-reservation />
    <checkout-form heading="Shipping" />
    <checkout-shipping-method />
    <checkout-bill-address-select @switchAddress="handleAddressSwitch" />
    <checkout-form :isSameAddress="isSameAddress" />
  </main>
</template>

<script>
import { defineComponent, ref } from "vue";
import CheckoutForm from "./CheckoutForm.vue";
import CheckoutHeadline from "./CheckoutHeadline.vue";
import CheckoutReservation from "./CheckoutReservation.vue";

import CheckoutBillAddressSelect from "./CheckoutBillAddressSelect.vue";
import CheckoutShippingMethod from "./CheckoutShippingMethod.vue";

export default defineComponent({
  components: {
    CheckoutForm,
    CheckoutHeadline,
    CheckoutReservation,
    CheckoutBillAddressSelect,
    CheckoutShippingMethod,
  },
  name: "CheckoutMainContent",
  setup() {
    const isSameAddress = ref(true);

    const handleAddressSwitch = () => {
      isSameAddress.value = !isSameAddress.value;
    };

    return {
      handleAddressSwitch,
      isSameAddress,
    };
  },
});
</script>
<style lang="scss" scoped>
main {
  align-self: center;
}
</style>
