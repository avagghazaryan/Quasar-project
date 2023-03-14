<template>
    <main class="flex column q-gutter-md col col-lg-4">
        <checkout-headline />
        <checkout-reservation />
        <checkout-form heading="Shipping" ref="myForm" />
        <checkout-shipping-method />
        <checkout-bill-address-select @switchAddress="handleAddressSwitch" />
        <checkout-form
            :isSameAddress="isSameAddress"
            heading="Billing"
            ref="myForm2"
        />
        <q-btn
            draggable
            dark-percentage="90"
            @click="$router.replace('/upsell') && handleFormSubmit"
            >Complete Order</q-btn
        >
    </main>
</template>

<script>
import { defineComponent, ref } from 'vue';
import CheckoutForm from './CheckoutForm.vue';
import CheckoutHeadline from './CheckoutHeadline.vue';
import CheckoutReservation from './CheckoutReservation.vue';

import CheckoutBillAddressSelect from './CheckoutBillAddressSelect.vue';
import CheckoutShippingMethod from './CheckoutShippingMethod.vue';

export default defineComponent({
    components: {
        CheckoutForm,
        CheckoutHeadline,
        CheckoutReservation,
        CheckoutBillAddressSelect,
        CheckoutShippingMethod,
    },
    name: 'CheckoutMainContent',
    setup() {
        const isSameAddress = ref(true);

        const handleAddressSwitch = () => {
            isSameAddress.value = !isSameAddress.value;
        };

        const myForm = ref(null);
        const myForm2 = ref(null);

        function validate() {
            myForm.value.validate().then(success => {
                if (success) {
                    console.log({ success });
                } else {
                    // oh no, user has filled in
                    // at least one invalid value
                }
            });
        }
        // to reset validations:
        function reset() {
            myForm.value.resetValidation();
        }

        const handleFormSubmit = e => {
            console.log(44);

            myForm.value.handleSubmit();
        };

        return {
            handleFormSubmit,
            handleAddressSwitch,
            isSameAddress,
            myForm,
            myForm2,
        };
    },
});
</script>
