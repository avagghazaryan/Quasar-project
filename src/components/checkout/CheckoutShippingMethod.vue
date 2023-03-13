<template>
  <q-card>
    <q-card-section class="flex column">
      <span class="text-h4">Shipping method</span>
      <div class="flex justify-between">
        <q-option-group :options="options" type="radio" v-model="method" />
        <div class="flex column q-gutter-md">
          <span>$10</span>
          <span>$20</span>
        </div>
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent, ref } from "vue";

const options = [
  { label: "Free shipping", value: true },
  { label: "DHL with price", value: false },
];

export default defineComponent({
  name: "CheckoutShippingMethod",
  props: {
    isSameAddress: { type: Boolean, default: true },
  },

  setup() {
    const method = ref(true);

    return {
      options,
      method,
    };
  },
});
</script>
