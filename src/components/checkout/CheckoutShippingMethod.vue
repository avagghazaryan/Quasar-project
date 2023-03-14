<template>
  <q-card>
    <q-card-section class="flex column q-gutter-sm">
      <span class="shipping-method-text">Shipping method</span>
      <div class="flex justify-between">
        <q-option-group
          class="option-group-texts"
          :options="options"
          type="radio"
          v-model="method"
        />
      </div>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent, ref } from "vue";
import "@fontsource/poppins";
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

<style scoped lang="scss">
.q-card {
  padding-left: 16px !important;
  box-shadow: none;
}
.shipping-method-text {
  font-family: "Poppins";
  font-weight: 500;
  font-size: 24px;
}

.option-group-texts {
  width: 100%;
  background: rgba(239, 240, 245, 0.4);
  border-radius: 16px;
  font-family: "Poppins";
  font-weight: 500;
}
</style>
