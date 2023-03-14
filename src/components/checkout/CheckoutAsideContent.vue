<template>
    <aside class="flex column q-gutter-md col col-lg-4">
        <checkout-subtotal />
        <div class="order-information">
            <span class="information-text">
                <img src="../../assets/key1.svg" class="safe-secure-icon" />
                Secure SSL Encryption & Guaranteed Safe Checkout
            </span>
            <checkout-payment-networks />
        </div>
        <checkout-features />
        <checkout-payment-form />
    </aside>
</template>

<script>
import { defineComponent } from 'vue';

import CheckoutSubtotal from './CheckoutSubtotal.vue';
import CheckoutPaymentNetworks from './CheckoutPaymentNetworks.vue';
import CheckoutFeatures from './CheckoutFeatures.vue';
import CheckoutPaymentForm from './CheckoutPaymentForm.vue';

export default defineComponent({
    components: {
        CheckoutSubtotal,
        CheckoutPaymentNetworks,
        CheckoutFeatures,
        CheckoutPaymentForm,
    },
    name: 'CheckoutAsideContent',
    setup() {
        return {};
    },
});
</script>

<style scoped lang="scss">
.order-information {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 20px;
    width: 595px;
    height: 145px;

    /* white */

    background: #ffffff;
    border-radius: 16px;

    .thank-you-text {
        font-family: 'Poppins';
        font-style: normal;
        font-weight: 600;
        font-size: 24px;
        line-height: 34px;
        text-align: center;
        color: #000034;
        @media (max-width: 663px) {
            font-family: 'Poppins';
            font-style: normal;
            font-weight: 600;
            font-size: 19px;
            line-height: 30px;
        }
    }
    .order-confirmed-text {
        font-family: 'Poppins';
        font-style: normal;
        font-weight: 500;
        font-size: 16px;
        line-height: 26px;
        text-align: center;
        color: #4b4e68;
    }
    .q-card {
        border: none;
        box-shadow: none;
        background: #ffffff;
    }
}
</style>
