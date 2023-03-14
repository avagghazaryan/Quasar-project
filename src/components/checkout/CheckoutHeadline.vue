<template>
  <q-card>
    <q-card-section class="flex column">
      <span class="heading">Checkout</span>
      <div class="dropdown-content hideShowBtn">
        <div class="dropdown">
          <img src="../../assets/shopping.svg" />
          <div>
            <q-btn-dropdown
              class="glossy"
              label=" Show order summary"
              v-model="showSummary"
            />
          </div>
        </div>
        <div class="price"><span>€69.00</span></div>
      </div>
      <checkout-subtotal v-if="showSummary" />
      <span class="attention"
        >Strong demand! Complete your order before it's too late!</span
      >
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent, ref } from "vue";
import "@fontsource/poppins";
import CheckoutSubtotal from "./CheckoutSubtotal.vue";

export default defineComponent({
  components: { CheckoutSubtotal },
  name: "CheckoutHeadline",
  setup() {
    const showSummary = ref(false);
    return {
      showSummary,
    };
  },
});
</script>

<style lang="scss" scoped>
.q-card {
  box-shadow: none;
  border: none;
  .heading {
    font-family: Poppins;
    font-size: 36px;
    font-weight: 700;
    padding: 0;
    margin-bottom: 50px;
  }
  .attention {
    font-family: Poppins;
    font-size: 20px;
    font-weight: 400;
    color: #4b4e68;
  }

  .hideShowBtn {
    display: none;
    @media (max-width: 880px) {
      display: flex;
    }
  }

  .dropdown-content {
    box-shadow: hide;
    border: none;
    @media (max-width: 880px) {
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: hide;
      border: none;
      padding: 8px;
      max-width: 100%;
      height: 74px;
      background: #ffffff;
      border: 1px solid #d6d8ee;
      border-radius: 20px;
    }
    .dropdown {
      display: flex;
      justify-content: flex-start;
      align-items: center;
      width: 100%;
      gap: 20px;

      @media (max-width: 550px) {
        width: 100%;
        gap: 0;
      }
      .glossy {
        font-family: "Poppins";
        font-weight: 500;
        font-size: 16px;
        background: rgb(252, 244, 244);
        @media (max-width: 550px) {
          font-size: 13px;
        }
      }
    }
    .price {
      display: flex;
      justify-content: flex-end;
      align-items: flex-end;
      font-weight: 600;
    }
  }
}
</style>
