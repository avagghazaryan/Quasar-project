<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-black">
      <article class="logo-wrapper">
        <q-img :src="logo" img-class="my-custom-image" class="logo" />
      </article>
    </q-header>
    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent } from "vue";
import logo from "../assets/logo.svg";

export default defineComponent({
  name: "CheckoutLayout",

  setup() {
    return {
      logo,
    };
  },
});
</script>

<style scoped lang="scss">
header {
  height: 80px;
  display: flex;
  align-items: center;
  .logo-wrapper {
    padding: 0 !important;
    width: 30%;
    display: flex;
    justify-content: end;
  }
  .logo {
    padding: 0 !important;
    width: 171px;
    height: 36px;

    @media (max-width: 500px) {
      width: 100px;
      height: 16px;
    }
  }
}
</style>
