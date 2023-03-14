<template>
  <q-form :onsubmit="handleSubmit" ref="checkoutForm">
    <q-page class="checkout-page flex justify-center q-gutter-lg wrap">
      <checkout-main-content class="col" />
      <checkout-aside-content
        @triggerSubmit="handleFormSubmit"
        class="reverse-wrap"
      />
    </q-page>
  </q-form>
</template>

<script>
import { Notify } from "quasar";
import CheckoutAsideContent from "src/components/checkout/CheckoutAsideContent.vue";
import CheckoutMainContent from "src/components/checkout/CheckoutMainContent.vue";
import { defineComponent, ref } from "vue";
import { useRouter } from "vue-router";

const createToaster = (message, color) => {
  Notify.create({
    html: "span",
    message,
    icon: "alarm_add",
    timeout: 2500,
    color: color,
    bgColor: "#45ac15",
    button: {
      label: "Undo",
      handler() {
        // Specify what to do when button is clicked/tapped
      },
      color: "#000",
    },
  });
};

export default defineComponent({
  name: "CheckoutPage",
  components: {
    CheckoutAsideContent,
    CheckoutMainContent,
  },
  setup() {
    const $router = useRouter();
    const checkoutForm = ref(null);

    const handleFormSubmit = () => {
      console.log("recieved");
      validate();
    };

    function validate() {
      checkoutForm.value
        .validate()
        .then((success) => {
          success && $router.replace("/upsell");
          return success
            ? createToaster("Purchase completed", "primary")
            : createToaster("Please fill purchase form", "negative");
        })
        .catch((err) => console.log(err));
    }
    // to reset validations:
    function reset() {
      checkoutForm.value.resetValidation();
    }

    return {
      checkoutForm,
      handleFormSubmit,
    };
  },
});
</script>

<style lang="scss" scoped>
.q-page {
  padding-top: 20px;
  background-color: #d6d8ea;
  > main {
    margin: 40px 0;
    max-width: 750px;
    min-width: 500px;
    background-color: #fff;
    border-radius: 16px;
    ::v-deep .q-card {
      margin: 0;
      margin: 0 40px;
    }
  }
  > aside {
    max-width: 450px;
    min-width: 400px;
  }

  //   @media (max-width: 1100px) {
  //     display: flex;
  //     flex-direction: column;
  //     align-items: center;
  //   }
}
h4 {
  padding-bottom: 0 !important;
}
aside {
  min-width: 25%;
  min-height: 100vh;
}

.productsInfoSection {
  padding: 5px 0;
}
.underline {
  margin-top: 20px;
  margin-bottom: 11px;
  height: 1px;
  background-color: #d6d8ee;
}
</style>
