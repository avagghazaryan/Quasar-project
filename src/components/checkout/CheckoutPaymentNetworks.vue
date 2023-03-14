<template>
    <q-card bordered class="wrap">
        <q-card-section class="flex no-wrap" v-if="!hideSSL">
            <!-- <span>ICON</span> -->
            <span>{{ paymentText }}</span>
        </q-card-section>
        <article class="avatar-group" aria-disabled="flex justify-evenly">
            <q-avatar
                v-for="network in paymentNetworks"
                :key="network.id"
                rounded
            >
                <img :src="network.src" :alt="network.name" />
            </q-avatar>
        </article>
    </q-card>
</template>

<script>
import { defineComponent } from 'vue';

import gago from '../../assets/master-card.svg';
import club from '../../assets/Club.svg';
import visa from '../../assets/visa.svg';
import paypal from '../../assets/paypal.svg';
import amex from '../../assets/amex.svg';
import jcb from '../../assets/jcb.svg';

const paymentNetworks = [
    {
        id: 0,
        name: 'MasterCard',
        src: gago,
    },
    {
        id: 1,
        name: 'Visa',
        src: visa,
    },
    {
        id: 2,
        name: 'PayPal',
        src: paypal,
    },
    {
        id: 3,
        name: 'AMEX',
        src: amex,
    },
    {
        id: 4,
        name: 'JCB',
        src: jcb,
    },
    {
        id: 5,
        name: 'DinersClub',
        src: club,
    },
];

export default defineComponent({
    name: 'CheckoutPaymentNetworks',
    props: {
        hideSSL: { type: Boolean, default: false },
        paymentText: { type: String },
    },
    setup() {
        return {
            paymentNetworks,
        };
    },
});
</script>

<style scoped lang="scss">
.wrap > div {
    display: none;
}
.avatar-group {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 7px;
}
</style>
