<template>
  <q-card class="jewellery-club-wrapper">
    <q-card-section class="jew-section">
      <span class="ultimate text-h6">The ultimate jewellery club</span>
      <span
        >Ornare rhoncus nunc ut felis. Faucibus dolor at ultrices tincidunt.
        Pulvinar sed justo et viverra pellentesque.</span
      >
      <article class="article-wrap">
        <div
          v-for="feat in billFeatures"
          :key="feat.id"
          class="flex justify-between"
        >
          <img src="../../assets/check.svg" alt="" />
          <span>{{ feat.info }}</span>
        </div>
      </article>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent } from "vue";
import "@fontsource/poppins";

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

<style scoped lang="scss">
.jewellery-club-wrapper {
  padding: 20px;
  font-size: 14px;
  font-weight: 400;
  border-radius: 16px;
  font-family: "Poppins";

  .ultimate {
    font-weight: 600;
    font-size: 18px;
  }

  .jew-section {
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .article-wrap {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: 5px;
    > div {
      display: flex;
      gap: 10px;
    }
  }
}
</style>
