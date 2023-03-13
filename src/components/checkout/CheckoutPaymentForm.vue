<template>
  <q-form @submit="handleSubmit" ref="formRef">
    <div class="flex column">
      <span class="text-h6">Payment Method</span>
      <div>
        <div class="credit flex column q-gutter-md">
          <div class="flex justify-between">
            <q-radio v-model="shape" val="card" label="Credit Card" />
            <checkout-payment-networks hideSSL />
          </div>
          <div v-if="shape === 'card'">
            <q-input
              rounded
              outlined
              :options="countryOpts"
              v-model:cardNumber="paymentOptions.cardNumber"
              label="Card number"
              lazy-rules
              :rules="[
                (val) => (val && val.length > 0) || 'Please type card number',
              ]"
            />
            <q-input
              rounded
              outlined
              :options="countryOpts"
              v-model:ownerName="paymentOptions.ownerName"
              label="Name on Card"
              lazy-rules
              :rules="[
                (val) => (val && val.length > 0) || 'Please type owner name',
              ]"
            />

            <div class="flex justify-stretch">
              <q-input
                v-model:expireDate="paymentOptions.expireDate"
                rounded
                outlined
                label="MM/YY"
                class="col q-mr-md"
                lazy-rules
                :rules="[
                  (val) =>
                    (val && val.length > 0) || 'Please type expiration date',
                ]"
              />
              <q-input
                type="number"
                v-model:cvv="paymentOptions.cvv"
                rounded
                outlined
                label="CVV"
                class="col inline"
                lazy-rules
                :rules="[(val) => (val && val.length > 0) || 'Please type CVV']"
              />
            </div>
          </div>
        </div>
      </div>
      <div class="flex no-wrap" style="color: red">
        <span class="q-mr-sm">Icon</span>
        <span class=""
          >By checking this box, I acknowledge that I have read and agree to the
          Terms of Service, and Monthly Billing Terms of this website and want
          to opt-in for the monthly billed Dream Collection Club®</span
        >
      </div>
    </div>

    <div class="flex justify-between">
      <q-radio v-model="shape" val="paypal" label="Paypal" />
      <checkout-payment-networks hideSSL />
    </div>
    <q-btn draggable dark-percentage="90" @click="handleFormSubmit"
      >Complete Order</q-btn
    >
  </q-form>
</template>

<script>
import { defineComponent, ref, reactive } from "vue";
import CheckoutPaymentNetworks from "./CheckoutPaymentNetworks.vue";

export default defineComponent({
  components: { CheckoutPaymentNetworks },
  name: "CheckoutPaymentForm",
  props: {
    heading: { type: String, default: "" },
    isSameAddress: { type: Boolean, default: true },
  },
  setup() {
    const formRef = ref(null);
    const shape = ref("card");
    const paymentOptions = reactive({
      cardNumber: "",
      ownerName: "",
      expireDate: "",
      cvv: null,
    });

    const handleSubmit = () => {
      console.log("submited");
      formRef.value.validate();
    };

    return {
      paymentOptions,
      formRef,
      handleSubmit,
      shape,
    };
  },
});
</script>
