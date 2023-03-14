<template>
  <q-card>
    <q-card-section
      class="flex column q-gutter-md"
      v-if="heading === 'Shipping'"
    >
      <span class="contact-info">Contact Information</span>
      <q-input
        v-model="checkoutOptions.email"
        rounded
        outlined
        label="Email Address"
        lazy-rules
        :rules="[
          (val) =>
            (val && val.length > 0 && isEmail(val)) ||
            'Enter a valid email address',
        ]"
      >
        <template v-slot:label>
          <q-icon name="fa-solid fa-envelope" />
          <span> Email Address</span>
        </template>
      </q-input>
      <q-input
        v-model="checkoutOptions.phone"
        rounded
        outlined
        label="Phone Number"
      >
        <template v-slot:label>
          <div>
            <q-icon name="fa-solid fa-phone-volume" />
            <span> Phone Number</span>
          </div>
        </template></q-input
      >
      <q-checkbox
        class="sign-up"
        v-model="checkoutOptions.useOffers"
        rounded
        outlined
        label="Sign up for exclusive offers and news"
      />
    </q-card-section>
    <q-card-section
      v-if="!isSameAddress || heading === 'Shipping'"
      class="flex column q-gutter-md"
    >
      <span v-if="heading" class="shipping-adress-text">
        {{ heading }} Address</span
      >
      <div class="flex column q-gutter-md">
        <q-select
          rounded
          outlined
          :options="countryOpts"
          v-model="checkoutOptions.country"
          label=""
        >
          <template v-slot:label>
            <div>
              <q-icon name="fa-solid fa-location-dot" />
              <span>Select a Country</span>
            </div>
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
              (val) =>
                (val && val.length > 0 && isValidName(val)) ||
                'Enter a first name',
            ]"
          >
            <template v-slot:label>
              <div>
                <q-icon name="fa-solid fa-user" />
                <span> First Name</span>
              </div>
            </template></q-input
          >
          <q-input
            v-model="checkoutOptions.lastName"
            rounded
            outlined
            label="Last Name"
            class="col inline"
            lazy-rules
            :rules="[
              (val) =>
                (val && val.length > 0 && isValidName(val)) ||
                'Enter a last name',
            ]"
          >
            <template v-slot:label>
              <div>
                <q-icon name="fa-solid fa-user" />
                <span> Last Name</span>
              </div>
            </template>
          </q-input>
        </div>
        <q-input
          v-model="checkoutOptions.address"
          rounded
          outlined
          label="Address"
        >
          <template v-slot:label>
            <div>
              <q-icon name="fa-solid fa-envelope-open" />
              <span> Address</span>
            </div>
          </template></q-input
        >
        <q-input
          v-model="checkoutOptions.apartment"
          rounded
          outlined
          label="Aparment, suit, etc (Optional)"
        >
          <template v-slot:label>
            <div>
              <q-icon name="fa-solid fa-building" />
              <span> Aparment, suit, etc (Optional)</span>
            </div>
          </template></q-input
        >
        <div class="flex justify-stretch">
          <q-input
            v-model="checkoutOptions.city"
            rounded
            outlined
            class="col q-mr-md"
            label=" City"
          />

          <q-input
            type="number"
            v-model="checkoutOptions.postalCode"
            rounded
            outlined
            class="col"
            label=" Postal Code"
          />
        </div>
      </div>
    </q-card-section>
  </q-card>
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

    const isEmail = (emailAdress) => {
      let regex = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
      return emailAdress.match(regex);
    };

    const isValidName = (name) => {
      let regex = /^[a-z ,.'-]+$/i;
      return name.match(regex);
    };

    return {
      countryOpts,
      checkoutOptions,
      formRef,
      isEmail,
      isValidName,
    };
  },
});
</script>
<style lang="scss" scoped>
.q-card {
  box-shadow: none;
  .q-card__section {
  }
}
.contact-info {
  font-family: "Poppins";
  font-weight: 500;
  font-size: 24px;
}

.sign-up {
  font-family: "Poppins";
  font-weight: 400;
  font-size: 16px;
}

.shipping-adress-text {
  font-family: "Poppins";
  font-weight: 500;
  font-size: 24px;
}
</style>
