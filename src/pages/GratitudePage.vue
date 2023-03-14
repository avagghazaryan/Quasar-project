<template>
  <q-layout class="wrapper">
    <div class="main-content">
      <div class="order-wrapper">
        <div class="dropdown-content">
          <div class="dropdown">
            <img src="../assets/shopping.svg" />
            <div class="q-pa-md">
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
        <q-img
          src="../assets/like.svg"
          img-class="my-custom-image"
          class="img-like"
        />
        <div class="order-information">
          <span class="thank-you-text text-h5 bold"
            >Thank you for your order
          </span>
          <span class="order-confirmed-text text-body1"
            >Your order is confirmed
          </span>
        </div>

        <q-btn
          class="back-to-shot-btn"
          color="black"
          icon-left="bi bi  user"
          text-color="white"
          icon="fa-solid fa-arrow-left"
          label="Back to Shop"
          @click="$router.replace('/upsell')"
        />
        <div class="order-detail-list">
          <q-list>
            <q-item>
              <q-item-section>
                <q-item-label caption>Name:</q-item-label>
              </q-item-section>
              <q-item-section>
                <q-item-label>Oleo Bone</q-item-label>
              </q-item-section>
            </q-item>

            <q-separator spaced inset />

            <q-item>
              <q-item-section>
                <q-item-label caption>Email:</q-item-label>
              </q-item-section>
              <q-item-section>
                <q-item-label lines="1">oleo_bone@gmail.com </q-item-label>
              </q-item-section>
            </q-item>

            <q-separator spaced inset />

            <q-item>
              <q-item-section>
                <q-item-label caption>Ship to:</q-item-label>
              </q-item-section>
              <q-item-section>
                <q-item-label lines="1">
                  4140 Parker Rd. Allentown, New Mexico 31134
                </q-item-label>
              </q-item-section>
            </q-item>

            <q-separator spaced inset />

            <q-item>
              <q-item-section>
                <q-item-label caption>Bill to:</q-item-label>
              </q-item-section>
              <q-item-section>
                <q-item-label lines="1">
                  4140 Parker Rd. Allentown, New Mexico 31134
                </q-item-label>
              </q-item-section>
            </q-item>

            <q-separator spaced inset />

            <q-item>
              <q-item-section>
                <q-item-label caption>payment:</q-item-label>
              </q-item-section>
              <q-item-section>
                <q-item-label> Credit Card </q-item-label>
              </q-item-section>
            </q-item>
          </q-list>
        </div>
      </div>
      <div class="wrapper-summary-information">
        <div class="order-summary"><CheckoutSubtotal /></div>
        <div class="order-information1">
          <span class="information-text">
            <img src="../assets/key1.svg" class="safe-secure-icon" />
            Secure SSL Encryption & Guaranteed Safe Checkout
          </span>
          <CheckoutPaymentNetworks />
        </div>
      </div>
    </div>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import CheckoutPaymentNetworks from "../components/checkout/CheckoutPaymentNetworks.vue";
import CheckoutSubtotal from "../components/checkout/CheckoutSubtotal.vue";
import "@fontsource/poppins";

export default defineComponent({
  name: "IndexPage",
  components: {
    CheckoutPaymentNetworks,
    CheckoutSubtotal,
  },
  setup() {
    const showSummary = ref(false);
    return { showSummary };
  },
});
</script>

<style scoped lang="scss">
.wrapper {
  height: 100%;
  width: 100%;
  padding: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #d6d8ea;
  @media (max-width: 1000px) {
    padding: 0px !important;
  }
}

.main-content {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100%;
  width: 100%;
  gap: 40px;

  @media (max-width: 1282px) {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }

  .order-wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 50px !important;
    gap: 34px;
    width: 50%;
    height: 80%;
    background: #ffffff;
    border-radius: 16px;

    .dropdown-content {
      display: none;
      @media (max-width: 1280px) {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 8px;
        max-width: 100%;
        height: 74px;
        background: #ffffff;
        border: 1px solid #d6d8ee;
        border-radius: 20px;
      }
      .dropdown {
        display: flex;
        justify-content: center;
        align-items: center;
        width: 100%;
        gap: 20px;

        @media (max-width: 550px) {
          width: 100%;
          gap: 0;
        }
        .glossy {
          all: initial;
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

    @media (max-width: 1000px) {
      width: 90%;
      height: 57%;
      margin-top: 10%;
    }
    @media (max-width: 663px) {
      width: 90%;
      height: 57%;
      margin-top: 20%;
    }

    .img-like {
      width: 167.07px;
      height: 166.43px;
    }

    .order-information {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 20px;

      .thank-you-text {
        font-family: "Poppins";
        font-style: normal;
        font-weight: 600;
        font-size: 24px;
        line-height: 34px;
        text-align: center;
        color: #000034;

        @media (max-width: 663px) {
          font-family: "Poppins";
          font-style: normal;
          font-weight: 600;
          font-size: 19px;
          line-height: 30px;
        }
      }
      .order-confirmed-text {
        font-family: "Poppins";
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 26px;
        text-align: center;
        color: #4b4e68;
      }
    }

    .back-to-shot-btn {
      width: 213px;
      height: 56px;
      border-radius: 16px;
      background: #000034;
      font-family: "Poppins";
      font-style: normal;
      font-weight: 600;
      font-size: 14px;
      text-transform: none;

      @media (max-width: 663px) {
        width: 313px;
        height: 42px;
      }

      @media (max-width: 350px) {
        width: 200px;
        height: 42px;
      }
    }

    .order-detail-list {
      width: 70%;
      background: rgba(239, 240, 245, 0.4);
      border-radius: 16px;
      font-family: "Poppins";
      font-style: normal;
      font-weight: 400;
      font-size: 14px;
      line-height: 24px;
      color: #000034;

      @media (max-width: 1000px) {
        width: 90%;
      }
      @media (max-width: 663px) {
        width: 90%;
      }
    }
  }

  .wrapper-summary-information {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    gap: 30px;
    width: 30%;
    height: 80%;

    @media (max-width: 1282px) {
      width: 60%;
      height: 80%;
    }

    @media (max-width: 1000px) {
      width: 90%;
      height: 80%;
    }
    @media (max-width: 770px) {
      width: 88%;
      height: 80%;
    }

    @media (max-width: 700px) {
      width: 80%;
      height: 80%;
    }

    @media (max-width: 400px) {
      width: 94%;
      height: 80%;
    }

    .order-summary {
      width: 100%;
      height: 60%;
      background: #ffffff;
      border-radius: 16px;

      ::v-deep .discount-field {
        display: none !important;
      }
      @media (max-width: 1282px) {
        display: none;
      }
    }

    .order-information1 {
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      gap: 20px;
      width: 100%;
      height: 145px;
      background: #ffffff;
      border-radius: 16px;

      @media (max-width: 1281px) {
        background: #ffffff;
        width: 100%;
        height: 125px;
      }

      @media (max-width: 663px) {
        width: 100%;
        height: 146px;
      }

      span {
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 10px;
      }

      .q-card {
        border: none;
        box-shadow: none;
        background: #ffffff;
      }
    }
  }
}
</style>
