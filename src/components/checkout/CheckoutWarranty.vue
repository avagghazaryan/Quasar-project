<template>
  <q-card class="flex justify-between">
    <q-card-section class="flex column">
      <span class="lifeteme"
        >Lifetime Warranty <q-icon class="fire-icon" name="warning"
      /></span>
      <span class="lifetime-descripthion"
        >Add a lifetime warranty & enjoy peace of mind for life with your dream
        collections order for just $4.99</span
      >
    </q-card-section>
    <q-card-actions>
      <q-btn class="apply-btn" label="Add- $4.99" @click="openToaster" />
    </q-card-actions>
  </q-card>
</template>
<script>
import { defineComponent } from "vue";
import { Notify } from "quasar";
import "@fontsource/poppins";

const openToaster = () => {
  Notify.create({
    message: `Lifetime Warranty is added successfully`,
    icon: "alarm_add",
    timeout: 2500,
    color: "primary",
    bgColor: "#45ac15",
    button: {
      label: "Undo",
      handler() {
        // Specify what to do when button is clicked/tapped
      },
    },
  });
};

export default defineComponent({
  name: "CheckoutWarranty",
  setup() {
    return { openToaster };
  },
});
</script>
<style lang="scss" scoped>
.q-card {
  margin: 16px 0 0 16px !important;
  background-color: #ebecf3;
  border-radius: 16px !important;
  .q-card__section {
    max-width: 70%;
  }
  .lifeteme {
    font-family: "Poppins";
    font-weight: 600;
    font-size: 20px;
  }
  .fire-icon {
    color: orange;
  }
  .lifetime-descripthion {
    font-family: "Poppins";
    font-weight: 400;
    font-size: 14px;
  }

  .apply-btn {
    flex-wrap: wrap;
    color: white;
    max-width: 115px;
    height: 62px;
    background: #000034;
    border-radius: 10px;
    font-size: 16px;
    text-transform: none;
    font-weight: 500;
    line-height: 20px;
    word-spacing: 25px;
  }
}
</style>
