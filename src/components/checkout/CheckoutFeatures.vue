<template>
  <q-card>
    <q-card-section class="flex column">
      <span class="text-h6">The ultimate jewellery club</span>
      <span
        >Ornare rhoncus nunc ut felis. Faucibus dolor at ultrices tincidunt.
        Pulvinar sed justo et viverra pellentesque.</span
      >
      <article>
        <div
          v-for="feat in billFeatures"
          :key="feat.id"
          class="flex justify-between"
        >
          <span>ICON</span>

          <span>{{ feat.info }}</span>
        </div>
      </article>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent } from "vue";

const billFeatures = [
  {
    id: 0,
    info: "Extra 10$ off!",
  },
  {
    id: 1,
    info: "Free shipping on marked club items!",
  },
  {
    id: 2,
    info: "Free returns on marked club items!",
  },
];

export default defineComponent({
  name: "CheckoutFeatures",
  setup() {
    return {
      billFeatures,
    };
  },
});
</script>
