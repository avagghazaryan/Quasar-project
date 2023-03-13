<template>
  <q-card>
    <q-card-section class="flex column">
      <span class="text-h4">Billing Address</span>
      <span>Specify the address for your payment option</span>
      <q-option-group
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
