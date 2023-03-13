<template>
  <q-form @submit="handleSubmit" ref="formRef">
    <div class="flex column" v-if="heading === 'Shipping'">
      <span class="contact-info">Contact Information</span>
      <q-input
        v-model="checkoutOptions.email"
        rounded
        outlined
        label="Email Address"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type email']"
      />
      <q-input
        v-model="checkoutOptions.phone"
        rounded
        outlined
        label="Phone Number"
        lazy-rules
        :rules="[(val) => (val && val.length > 0) || 'Please type email']"
      />
      <q-checkbox
        v-model="checkoutOptions.useOffers"
        rounded
        outlined
        label="Sign up for exclusive offers and news"
      />
    </div>
    <div
      v-if="(heading === 'Billing' && !isSameAddress) || heading === 'Shipping'"
    >
      <div class="flex column q-gutter-md">
        <span class="text-h6">{{ heading }} Address</span>
        <q-select
          rounded
          outlined
          :options="countryOpts"
          v-model="checkoutOptions.country"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please type email']"
        >
          <template v-slot:append>
            <q-avatar>
              <img src="https://cdn.quasar.dev/logo-v2/svg/logo.svg" />
            </q-avatar>
          </template>
        </q-select>
        <div class="flex justify-stretch">
          <q-input
            v-model="checkoutOptions.firstName"
            rounded
            outlined
            label="First Name"
            class="col q-mr-md"
            lazy-rules
            :rules="[
              (val) => (val && val.length > 0) || 'Please type your first name',
            ]"
          />
          <q-input
            v-model="checkoutOptions.lastName"
            rounded
            outlined
            label="Last Name"
            class="col inline"
            lazy-rules
            :rules="[
              (val) => (val && val.length > 0) || 'Please type your last name',
            ]"
          />
        </div>
        <q-input
          v-model="checkoutOptions.address"
          rounded
          outlined
          label="Address"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please select address']"
        />
        <q-input
          v-model="checkoutOptions.apartment"
          rounded
          outlined
          label="Aparment, suit, etc (Optional)"
        />
        <div class="flex justify-stretch">
          <q-input
            v-model="checkoutOptions.city"
            rounded
            outlined
            class="col q-mr-md"
            label="City"
            lazy-rules
            :rules="[(val) => (val && val.length > 0) || 'Please type city']"
          >
            <template v-slot:append>
              <span>City</span>
            </template>
          </q-input>
          <q-input
            type="number"
            v-model="checkoutOptions.postalCode"
            rounded
            outlined
            class="col"
            label="Postal Code"
            lazy-rules
            :rules="[
              (val) =>
                (val && val !== null && val !== '' && val.length > 0) ||
                'Please type postalCode',
            ]"
          >
          </q-input>
        </div>
      </div>
    </div>
  </q-form>
</template>

<script>
import { defineComponent, ref } from "vue";
import "@fontsource/poppins";

const countryOpts = ["Armenia", "USA", "Canada"];

export default defineComponent({
  name: "CheckoutForm",
  props: {
    heading: { type: String, default: "" },
    isSameAddress: { type: Boolean, default: true },
  },
  setup() {
    const formRef = ref(null);
    const checkoutOptions = ref({
      email: "",
      phone: "",
      useOffers: false,
      country: "",
      firstName: "",
      lastName: "",
      address: "",
      city: "",
      postalCode: null,
    });

    const handleSubmit = () => {
      console.log("submited");
      formRef.value.validate();
    };

    return {
      countryOpts,
      checkoutOptions,
      formRef,
      handleSubmit,
    };
  },
});
</script>
<style lang="scss" scoped>
.q-form {
  box-shadow: none;
  border: none;

  > div {
    box-shadow: none;
    border: none;
    > span {
      font-size: 24px;
      color: #000034;
    }
    .q-input,
    .q-select {
      * {
        border: none;
        box-shadow: none;
      }
      max-height: 56px;
      background-color: #ffffff;
      color: #84849a;
      font-size: 16px;
      font-family: "Poppins";
    }
    > .q-checkbox {
      font-family: "Poppins";
      font-weight: 400;
      font-size: 16px;
      color: #4b4e68;
    }
    > div {
      span {
        font-family: "Poppins";
        font-weight: 500;
        font-size: 24px;
        line-height: 34px;
        color: #000034;
      }
    }
  }
}
</style>
