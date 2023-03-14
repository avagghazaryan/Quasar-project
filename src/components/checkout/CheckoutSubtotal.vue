<template>
    <q-card class="order-summary-wrapper">
        <q-card-section class="flex column productsInfoSection">
            <span class="order-summary">Order Summary </span>

            <article
                v-for="item in products"
                :key="item.id"
                class="flex justify-stretch"
            >
                <div class="nike-sneakers-wrapper">
                    <img :src="item.src" :alt="item.name" />
                    <span>Nike Sneakers</span>
                </div>
                <span class="nike-price">$69.00</span>
            </article>
            <div class="discount-field">
                <q-input
                    class="input-field"
                    rounded
                    outlined
                    placeholder="Discount code"
                    v-model="inputText"
                />
                <q-btn class="apply-btn" label="Apply" />
            </div>
        </q-card-section>
        <q-card-section class="totalPrice flex column productsInfoSection">
            <div class="line">
                <span>Subtotal </span>
                <span>Shipping</span>
                <span>Discount</span>
            </div>
            <div class="line price">
                <span>€69.00</span>
                <span> - -</span>
                <span> - -</span>
            </div>
            <div class="hart-line"></div>
            <div class="total">
                <span>Total</span>
                <span class="price">€69.00</span>
            </div>
        </q-card-section>
    </q-card>
</template>

<script>
import { defineComponent } from 'vue';
import '@fontsource/poppins';

import nike1 from '../../assets/Nike1.svg';

const products = [
    {
        id: 0,
        name: 'Nike sneakers',
        price: 120.9,
        src: nike1,
    },
];

export default defineComponent({
    name: 'CheckoutSubtotal',
    setup() {
        return {
            products,
            inputText: '',
        };
    },
});
</script>

<style scoped lang="scss">
.order-summary-wrapper {
    background: #ffffff;
    border-radius: 16px;
    width: 595px;
    font-family: 'Poppins';
}

.productsInfoSection {
    gap: 15px;
}

.order-summary {
    font-family: 'Poppins';
    font-size: 24px;
    font-weight: 500;
    color: #000034;
}

article {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;

    .nike-sneakers-wrapper {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        gap: 15px;
    }
    .nike-price {
        display: flex;
        justify-content: flex-end;
        align-items: flex-end;
        font-weight: 600;
    }
}

.discount-field {
    display: flex;
    justify-content: space-between;
    gap: 24px;

    .input-field {
        width: 361px;
        height: 56px;
        background: #ffffff;
        border: 1.5px solid #ebecf3;
        border-radius: 16px;
        box-shadow: none;
        border: none;
    }
    .apply-btn {
        width: 130px;
        height: 56px;
        padding: 18px 40px;
        gap: 10px;
        border-radius: 16px;
        color: white;
        background: #000034;
        font-family: 'Poppins';
        font-weight: 600;
        font-size: 16px;
        text-transform: none;
    }
}

.totalPrice {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;

    .line {
        display: flex;
        flex-direction: column;
        gap: 15px;
        font-size: 16px;
        font-weight: 400;
        font-family: Poppins;
    }
    .price {
        font-weight: 600;
    }
}
.hart-line {
    width: 595px;
    border: 1px solid #d6d8ea;
}
.total {
    display: flex;
    justify-content: space-between;
    width: 100%;
    font-size: 16px;
    font-weight: 500;
}
</style>
