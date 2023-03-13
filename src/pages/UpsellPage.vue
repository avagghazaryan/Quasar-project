<template>
  <q-layout class="wrapper">
    <div class="slider-wrap">
      <q-carousel
        class="slider"
        draggable="false"
        v-model="slide"
        animated
        infinite
        :autoplay="autoplay"
        arrows
        transition-prev="slide-right"
        transition-next="slide-left"
        @mouseenter="autoplay = false"
        @mouseleave="autoplay = true"
      >
        <q-carousel-slide :name="1" img-src="../assets/product1.svg" />
        <q-carousel-slide :name="2" img-src="../assets/product1.svg" />
      </q-carousel>
    </div>
    <div class="quantity-wrapper">
      <div class="price-field">
        <span>Price:</span>
        <span class="price">${{ purchase }}</span>
        <span class="percent">-80%</span>
      </div>
      <div class="quantity-field">
        <div class="counter-field">
          <span class="quantity-text">Quantity:</span>
          <q-btn
            :disable="isDecrementDisabled"
            class="plus-minus-btn"
            text-color="black"
            color="white"
            @click="calculatePercent"
          >
            -</q-btn
          >
          <span class="quantity-text"> {{ count }} </span>

          <q-btn
            class="plus-minus-btn"
            text-color="black"
            color="white"
            @click="calculatePercent"
          >
            +</q-btn
          >
        </div>
      </div>
    </div>
    <div class="information">
      <span>
        Ornare rhoncus nunc ut felis. Faucibus dolor at ultrices tincidunt.
        Pulvinar sed justo et viverra pellentesque.
      </span>
      <span>
        Mauris augue nulla proin vel a. Facilisis fringilla molestie dignissim
        elit orci malesuada. Lorem sit sagittis vitae nulla id. Mauris ipsum sed
        sed faucibus. Nulla amet metus gravida orci faucibus nisl eros arcu
        lorem. Nullam ornare molestie nam id gravida volutpat bibendum sem
        feugiat. Neque vulputate in et maecenas porta mi tellus. In massa
        porttitor urna quis volutpat at.
      </span>
    </div>

    <div class="support-wrapper">
      <div class="safe-secure"></div>

      <div class="support">
        <img src="../assets/support1.svg" />
        <div class="support-text">
          <span class="support-text-24-7">24/7</span>
          <span>Support</span>
        </div>
      </div>
    </div>

    <div class="btn-group">
      <q-btn
        class="confirm-btn"
        text-color="white"
        color="black"
        label="Yes, I want"
        @click="$router.replace('/checkout')"
      />

      <q-item-label class="reject" @click="$router.replace('/gratitude')"
        >No, Thanks</q-item-label
      >
    </div>
  </q-layout>
</template>

<script>
import { defineComponent } from "vue";
import "@fontsource/poppins";
import { ref } from "vue";

export default defineComponent({
  name: "IndexPage",
  setup() {
    const purchase = ref(50);
    const count = ref(1);
    const isDecrementDisabled = ref(false);

    const calculatePercent = (e) => {
      if (e.target.textContent == " +") {
        isDecrementDisabled.value = false;
        count.value += 1;
        purchase.value += 50;
      } else {
        if (count.value <= 1) {
          isDecrementDisabled.value = true;
        } else {
          count.value -= 1;
          purchase.value -= 50;
        }
      }
    };

    return {
      purchase,
      count,
      isDecrementDisabled,
      slide: ref(1),
      autoplay: ref(true),
      calculatePercent,
    };
  },
});
</script>

<style scoped lang="scss">
.wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 40px;
  background-color: #d6d8ea;
}

.slider-wrap {
  margin-top: 8%;
  .slider {
    background-color: #d6d8ea;
    width: 790px;
    height: 520px;
    @media (max-width: 800px) {
      width: 664px;
      height: 437px;
    }
    @media (max-width: 663px) {
      width: 343px;
      height: 226px;
    }
  }
  @media (max-width: 800px) {
    margin-top: 16%;
  }
  @media (max-width: 663px) {
    margin-top: 26%;
  }
}

.quantity-wrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 25px;
  width: 790px;
  height: 225px;
  background-color: #ffffff;
  border-radius: 16px;

  @media (max-width: 800px) {
    width: 664px;
    height: 225px;
  }
  @media (max-width: 663px) {
    width: 343px;
    height: 225px;
  }

  .price-field {
    display: flex;
    gap: 10px;
    color: #000034;
    font-family: "Poppins";
    font-style: normal;
    font-weight: 500;
    font-size: 20px;
    line-height: 30px;

    .price {
      font-weight: bold;
      font-size: 30px;
    }

    .percent {
      display: flex;
      align-items: center;
      justify-content: center;
      width: 84px;
      height: 36px;
      background: #eff0f5;
      border-radius: 8px;
    }
  }

  .quantity-field {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 5px;
    width: 540px;
    height: 80px;
    background: #eff0f5;

    @media (max-width: 800px) {
      width: 584px;
      height: 80px;
    }
    @media (max-width: 663px) {
      width: 311px;
      height: 80px;
    }

    .quantity-text {
      font-weight: 500;
      font-size: 20px;
      line-height: 30px;
    }

    .counter-field {
      display: flex;
      justify-content: center;
      align-items: center;
      color: black;
      gap: 30px;
      opacity: 0.5;
      border-radius: 16px;

      .plus-minus-btn {
        font-size: 20px;
        width: 57px;
        height: 50px;
      }
    }
  }
}

.information {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  width: 790px;
  height: 228px;
  color: #4b4e68;
  font-weight: 500;
  font-size: 19px;
  line-height: 28px;
  font-family: "Poppins";
  font-style: normal;

  @media (max-width: 800px) {
    width: 664px;
    height: 208px;
  }
  @media (max-width: 663px) {
    width: 343px;
    height: 336px;
  }
}

.support-wrapper {
  display: flex;
  gap: 30px;

  @media (max-width: 663px) {
    margin-top: 15%;
    display: flex;
    gap: 15px;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  .safe-secure {
    width: 475px;
    height: 140px;
    background: #ffffff;
    border-radius: 16px;

    @media (max-width: 800px) {
      width: 394px;
      height: 140px;
    }
    @media (max-width: 663px) {
      width: 343px;
      height: 105px;
    }
  }

  .support {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 33px;
    width: 285px;
    height: 140px;
    background: #ffffff;
    border-radius: 16px;

    @media (max-width: 800px) {
      width: 250px;
      height: 140px;
    }
    @media (max-width: 663px) {
      display: flex;
      justify-content: flex-start;
      width: 343px;
      height: 105px;
    }

    .support-text {
      display: flex;
      flex-direction: column;
      width: 80px;
      height: 60px;
      font-family: "Poppins";
      font-style: normal;
      font-size: 20px;
      line-height: 30px;
      color: #000034;
    }

    .support-text-24-7 {
      font-weight: 600;
    }
  }
}

.btn-group {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 30px;
  margin-bottom: 100px;
  font-family: "Poppins";

  @media (max-width: 663) {
    display: flex;
    align-items: flex-start;
    justify-content: flex-start;
  }

  .confirm-btn {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 21.7143px 54.2857px;
    gap: 13.57px;
    width: 281.29px;
    height: 76.43px;
    flex: none;
    order: 0;
    flex-grow: 0;
    border-radius: 16px;
    font-style: normal;
    font-weight: 600;
    font-size: 24.4286px;
    line-height: 33px;

    @media (max-width: 663px) {
      text-decoration: none;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 11px 30px;
      width: 343px;
      height: 42px;
    }
  }
  .reject {
    width: 101px;
    height: 24px;
    font-weight: 600;
    font-size: 18px;
    font-style: normal;
    color: #4b4e68;
  }
}
</style>
