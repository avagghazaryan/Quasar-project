<template>
  <q-card>
    <q-card-section class="flex column q-gutter-sm">
      <span class="billing-adress-text">Billing Address</span>
      <span class="specify-adrees-text"
        >Specify the address for your payment option</span
      >
      <q-option-group
        class="billing-option-group"
        :options="options"
        type="radio"
        :model-value="address"
        @update:model-value="changeAddress"
      />
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent, ref } from "vue";
import "@fontsource/poppins";
const options = [
  { label: "Same as shipping address", value: true },
  { label: "Use a different billing address", value: false },
];

export default defineComponent({
  name: "CheckoutBillAddressSelect",
  props: {
    isSameAddress: { type: Boolean, default: true },
  },
  emits: ["switchAddress"],

  setup(props, { emit }) {
    const address = ref(true);
    const changeAddress = (e) => {
      console.log(e);
      address.value = !address.value;
      emit("switchAddress");
    };

    return {
      options,
      address,
      changeAddress,
    };
  },
});
</script>

<style scoped lang="scss">
.q-card {
  padding-left: 16px !important;
  box-shadow: none;
}
.billing-adress-text {
  font-family: "Poppins";
  font-weight: 500;
  font-size: 24px;
}
.specify-adrees-text {
  font-family: "Poppins";
  font-weight: 400;
  font-size: 14px;
}
.billing-option-group {
  width: 100%;
  border-radius: 16px;
  background: rgba(239, 240, 245, 0.4);
  font-family: "Poppins";
  font-weight: 500;
  font-size: 16px;
}
</style>
