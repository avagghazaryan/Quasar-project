<template>
  <q-page class="flex justify-center q-gutter-lg">
    <checkout-main-content />
    <checkout-aside-content />
  </q-page>
</template>

<script>
import CheckoutAsideContent from "src/components/checkout/CheckoutAsideContent.vue";
import CheckoutMainContent from "src/components/checkout/CheckoutMainContent.vue";
import { defineComponent } from "vue";

export default defineComponent({
  name: "CheckoutPage",
  components: {
    CheckoutAsideContent,
    CheckoutMainContent,
  },
});
</script>

<style lang="scss" scoped>
.q-page {
  > main {
    max-width: 40%;
    min-width: 35%;
  }
  > aside {
    max-width: 35%;
    min-width: 20%;
  }
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
