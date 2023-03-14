<template>
  <div class="payment-form" @submit="handleSubmit" ref="formRef">
    <div class="payment-method-wrapper">
      <span class="payment-method-text">Payment Method</span>

      <div class="credit-card-wrapper">
        <div class="credit flex column q-gutter-md">
          <div class="flex justify-between items-center q-gutter-sm">
            <q-radio v-model="shape" val="card" label="Credit Card" />
            <checkout-payment-networks hideLastItems />
          </div>
          <div v-if="shape === 'card'" class="flex column q-gutter-md">
            <q-input
              rounded
              outlined
              :options="countryOpts"
              v-model="paymentOptions.cardNumber"
              label="2587 9860 2354"
              lazy-rules
              :rules="[
                (val) =>
                  (val && val.length > 0 && validateCreditCard(val)) ||
                  'Enter valid card number',
              ]"
            >
              <template v-slot:label>
                <div>
                  <q-icon name="fa-solid fa-credit-card" />
                  <span> 2587 9860 2354</span>
                </div>
              </template>
            </q-input>
            <q-input
              rounded
              outlined
              :options="countryOpts"
              v-model="paymentOptions.ownerName"
              label="Name on the card"
            >
              <template v-slot:label>
                <div>
                  <q-icon name="fa-solid fa-user" />
                  <span> Name on the card</span>
                </div>
              </template>
            </q-input>
            <div class="flex justify-stretch">
              <q-input
                v-model="paymentOptions.expireDate"
                rounded
                outlined
                label="MM/YY"
                class="col q-mr-md"
              >
                <template v-slot:label>
                  <div>
                    <q-icon name="fa-solid fa-calendar-days" />
                    <span> MM/YY</span>
                  </div>
                </template>
              </q-input>
              <q-input
                type="number"
                v-model="paymentOptions.cvv"
                rounded
                outlined
                label="CVV"
                class="col inline"
              >
                <template v-slot:label>
                  <div>
                    <q-icon name="fa-solid fa-lock" />
                    <span> CVV</span>
                  </div>
                </template>
              </q-input>
            </div>
          </div>
        </div>
      </div>
      <div class="paypal">
        <q-radio v-model="shape" val="paypal" label="Paypal" />
        <img class="paypal-icon" src="../../assets/paypal1.svg" />
      </div>
      <div class="check-box">
        <q-checkbox v-model="teal" color="black" />
        <span
          >By checking this box, I acknowledge that I have read and agree to the
          <span class="bold-text">Terms of Service,</span> and
          <span class="bold-text">Monthly Billing Terms</span> of this website
          and want to opt-in for the monthly billed Dream Collection Club®</span
        >
      </div>
      <q-btn
        class="complete-btn"
        draggable
        dark-percentage="90"
        @click="triggerFormSubmit"
        >Complete Purchase</q-btn
      >
    </div>
  </div>
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
  emits: ["triggerSubmit"],

  setup(props, { emit }) {
    const formRef = ref(null);
    const shape = ref("card");

    const triggerFormSubmit = () => {
      emit("triggerSubmit");
    };
    const validateCreditCard = (card) => {
      console.log(card);
      let regex = /\b\d{12,16}\b/i;
      return card.match(regex);
    };
    const paymentOptions = reactive({
      cardNumber: "",
      ownerName: "",
      expireDate: "",
      cvv: null,
    });

    return {
      teal: ref(true),
      paymentOptions,
      formRef,
      triggerFormSubmit,
      validateCreditCard,
      shape,
    };
  },
});
</script>

<style scoped lang="scss">
.payment-form {
  padding: 25px;
  display: flex;
  flex-direction: column;
  gap: 20px;
  background: #ffffff;
  border-radius: 16px;
}
.payment-method-text {
  font-family: "Poppins";
  font-weight: 500;
  font-size: 24px;
  color: #000034;
}
.payment-method-wrapper {
  display: flex;
  flex-direction: column;
  align-content: center;
  flex-wrap: wrap;
  align-items: flex-start;
  gap: 20px;
  margin: 8px;
}

.credit-card-wrapper {
  display: flex;
  width: 100%;
  flex-direction: column;
  background: rgba(239, 240, 245, 0.4);
  border-radius: 16px;

  .credit {
    display: flex;
    gap: 5px;
  }
}

.q-card {
  border: none;
  box-shadow: none;
  background: none;
}

.paypal {
  display: flex;
  justify-content: space-between;
  width: 100%;
  align-items: center;
  background: rgba(239, 240, 245, 0.4);
  border-radius: 16px;
}

.check-box {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  flex-wrap: nowrap;
  .bold-text {
    font-weight: 600;
  }
}

.complete-btn {
  border-radius: 16px;
  font-weight: 600;
  font-size: 16px;
  font-family: "Poppins";
  background: #000034;
  color: #ffffff;
  text-transform: none;
}
</style>
