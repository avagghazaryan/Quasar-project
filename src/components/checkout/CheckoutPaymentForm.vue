<template>
    <q-form class="payment-form" @submit="handleSubmit" ref="formRef">
        <div class="payment-method-wrapper">
            <span class="payment-method-text">Payment Method</span>

            <div class="credit-card-wrapper">
                <div class="credit flex column q-gutter-md">
                    <div class="flex justify-between">
                        <q-radio
                            v-model="shape"
                            val="card"
                            label="Credit Card"
                        />
                        <checkout-payment-networks hideSSL />
                    </div>
                    <div v-if="shape === 'card'">
                        <q-input
                            class="input-field"
                            rounded
                            outlined
                            :options="countryOpts"
                            v-model:cardNumber="paymentOptions.cardNumber"
                            label="2587 9860 2354"
                            lazy-rules
                            :rules="[
                                val =>
                                    (val && val.length > 0) ||
                                    'Please type card number',
                            ]"
                        >
                            <template v-slot:prepend>
                                <q-icon name="bi bi-person" />
                            </template>
                        </q-input>
                        <q-input
                            rounded
                            outlined
                            :options="countryOpts"
                            v-model:ownerName="paymentOptions.ownerName"
                            label="Name on the card"
                            lazy-rules
                            :rules="[
                                val =>
                                    (val && val.length > 0) ||
                                    'Please type owner name',
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
                                    val =>
                                        (val && val.length > 0) ||
                                        'Please type expiration date',
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
                                :rules="[
                                    val =>
                                        (val && val.length > 0) ||
                                        'Please type CVV',
                                ]"
                            />
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
                    >By checking this box, I acknowledge that I have read and
                    agree to the
                    <span class="bold-text">Terms of Service,</span> and
                    <span class="bold-text">Monthly Billing Terms</span> of this
                    website and want to opt-in for the monthly billed Dream
                    Collection Club®</span
                >
            </div>
            <q-btn
                class="complete-btn"
                draggable
                dark-percentage="90"
                @click="handleFormSubmit"
                >Complete Purchase</q-btn
            >
        </div>
    </q-form>
</template>

<script>
import { defineComponent, ref, reactive } from 'vue';
import CheckoutPaymentNetworks from './CheckoutPaymentNetworks.vue';

export default defineComponent({
    components: { CheckoutPaymentNetworks },
    name: 'CheckoutPaymentForm',
    props: {
        heading: { type: String, default: '' },
        isSameAddress: { type: Boolean, default: true },
    },
    setup() {
        const formRef = ref(null);
        const shape = ref('card');
        const paymentOptions = reactive({
            cardNumber: '',
            ownerName: '',
            expireDate: '',
            cvv: null,
        });

        const handleSubmit = () => {
            console.log('submited');
            formRef.value.validate();
        };

        return {
            teal: ref(true),
            paymentOptions,
            formRef,
            handleSubmit,
            shape,
        };
    },
});
</script>

<style scoped lang="scss">
.payment-form {
    display: flex;
    flex-direction: column;
    gap: 20px;
    width: 595px;
    height: 656px;
    background: #ffffff;
    border-radius: 16px;
}
.payment-method-text {
    font-family: 'Poppins';
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
    flex-direction: column;
    width: 515px;
    background: rgba(239, 240, 245, 0.4);
    border-radius: 16px;

    .credit {
        display: flex;
        gap: 20px;

        .input-field {
            display: flex;
        }
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
    align-items: center;
    width: 515px;
    height: 64px;
    background: rgba(239, 240, 245, 0.4);
    border-radius: 16px;

    .paypal-icon {
    }
}

.check-box {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
    flex-wrap: nowrap;
    width: 483px;

    .bold-text {
        font-weight: 600;
    }
}

.complete-btn {
    width: 515px;
    height: 56px;
    border-radius: 16px;
    font-weight: 600;
    font-size: 16px;
    font-family: 'Poppins';
    background: #000034;
    color: #ffffff;
    text-transform: none;
}
</style>
