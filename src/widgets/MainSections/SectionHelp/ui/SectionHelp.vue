<script lang="ts">
import { BaseContainer, BaseAnimation, BaseButton } from "@/shared/ui";
import Wave from "../images/wave.png";
import VitalBox from "../images/vital-box.png";
import { isTablet } from "@/shared/lib";
import { ref } from "vue";

export default {
  components: {
    BaseContainer,
    BaseAnimation,
    BaseButton,
  },
  data() {
    return {
      Wave,
      VitalBox,
      isTablet,
    };
  },
  setup() {
    const count = ref(1);
    const incrementCount = () => (count.value += 1);
    const decrementCount = () => {
      count.value - 1 < 1 ? (count.value = 1) : (count.value -= 1);
    };

    return {
      count,
      incrementCount,
      decrementCount,
    };
  },
};
</script>

<template>
  <section class="health">
    <div class="health__wave">
      <img :src="Wave" alt="wave" />
    </div>
    <div class="health__wrapper">
      <BaseContainer>
        <div class="health__content">
          <div class="health__box">
            <BaseAnimation :delay="200">
              <h2>Vital for your health!</h2>
            </BaseAnimation>
            <div class="health__subtitle">
              <BaseAnimation :delay="400">
                <p>
                  Solle<b>Vital®</b> is a premium plant blend consisting of three balanced
                  ingredient groups: <b>adaptogens, trace minerals,</b> and our
                  chlorophyll blend.
                </p>
              </BaseAnimation>
              <BaseAnimation :delay="600">
                <p>
                  These blends work together to provide essential nutrients that
                  strengthen core body systems such as the circulatory, digestive,
                  respiratory and immune systems, promote recovery, and lift energy and
                  mood.
                </p>
              </BaseAnimation>
            </div>
            <BaseAnimation :delay="700" v-if="isTablet">
              <div class="health__img">
                <img :src="VitalBox" alt="VitalBox" />
              </div>
            </BaseAnimation>
            <BaseAnimation :delay="800">
              <div class="qty">
                <div class="qty__wrap">
                  <p class="qty__title"><strong>Qty</strong> (sticks)</p>
                  <div class="qty__price">
                    <div class="qty__switcher">
                      <button class="active" type="button">30</button>
                      <button type="button">100</button>
                    </div>
                    <p class="qty__value"><b>$47.25</b> USD</p>
                  </div>
                </div>
                <div class="qty__box">
                  <BaseButton class="qty__button">Add to cart</BaseButton>
                  <div class="qty__counter">
                    <button @click="decrementCount" type="button">-</button>
                    <span>{{ count }}</span>
                    <button @click="incrementCount" type="button">+</button>
                  </div>
                </div>
                <div class="qty__discover">
                  <p>
                    Discover your custom product recommendations when you take our quiz!
                  </p>
                  <a href="https://www.sollenaturals.com/take-our-quiz">Take the Quiz</a>
                </div>
              </div>
            </BaseAnimation>
          </div>
          <BaseAnimation variant="opacity" :delay="400" v-if="!isTablet">
            <div class="health__img">
              <img :src="VitalBox" alt="VitalBox" />
            </div>
          </BaseAnimation>
        </div>
      </BaseContainer>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";
.health {
  position: relative;
  padding-top: toRem(164);

  @media (max-width: $mobile) {
    padding-top: toRem(64);
  }

  &__wave {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;

    & img {
      width: 100%;
      aspect-ratio: 1604 / 417;
    }
  }

  &__wrapper {
    position: relative;
    z-index: $zIndex_1;
    background-color: $white;
  }

  &__content {
    display: grid;
    grid-template-columns: minmax(toRem(524), 1fr) 1fr;
    align-items: center;
    justify-content: space-between;
    gap: toRem(35);
  }

  &__box {
    @include flexColumn();
    row-gap: toRem(24);
  }

  &__subtitle {
    @include flexColumn();
    row-gap: toRem(24);
    line-height: 168.75%; /* 27/16 */
  }

  &__img {
    text-align: center;

    @media (max-width: $tablet) {
      margin-top: toRem(24);
    }

    & img {
      max-width: toRem(610);
      width: 100%;
      height: auto;
      aspect-ratio: 610 / 532;
      object-fit: contain;
      object-position: center;
    }
  }
}

.qty {
  @include flexColumn();
  row-gap: toRem(32);

  &__wrap {
    @include flexColumn();
    row-gap: toRem(12);
  }

  &__title {
    font-size: toRem(14);

    & strong {
      font-size: toRem(16);
      font-weight: 600;
    }
  }

  &__price {
    @include flexRow(center);
    column-gap: toRem(26);
  }

  &__switcher {
    @include flexRow(center);
    column-gap: toRem(4);
    background-color: $parchment_cream;
    border-radius: toRem(30);
    width: toRem(72);

    & button {
      @include flexRow(center, center);
      width: toRem(36);
      height: toRem(36);
      font-size: toRem(14);
      border-radius: 50%;
      color: #bcbab1;
      transition: color $transition;

      @media (any-hover: hover) {
        &:hover {
          color: $mainColor;
        }
      }

      &.active {
        color: $mainColor;
        background-color: #bcbab1;
      }
    }
  }

  &__value {
    font-size: toRem(24);
    font-weight: 300;

    & b {
      font-weight: 400;
    }
  }

  &__box {
    @include flexRow(center);
    column-gap: toRem(12);
  }

  &__button {
    font-size: toRem(14);
    letter-spacing: em(0.35);
    font-weight: 400;
    padding: toRem(7.5) toRem(30);
    color: $mainColor;
  }

  &__counter {
    @include flexRow(center);
    column-gap: toRem(2);
    border: toRem(1) solid $accent;
    border-radius: toRem(30);
    padding: toRem(4) toRem(9);
    font-size: toRem(14);

    & > button {
      display: inline-block;
      width: toRem(19);
      height: toRem(25);
      transition: opacity $transition;

      @media (any-hover: hover) {
        &:hover {
          opacity: 0.8;
        }
      }
    }

    & > span {
      display: inline-block;
      text-align: center;
      width: toRem(14);
      height: toRem(25);
    }
  }

  &__discover {
    font-size: toRem(14);

    & > a {
      color: #5fafbb;
      text-decoration: underline;
      transition: opacity $transition;

      @media (any-hover: hover) {
        &:hover {
          opacity: 0.8;
        }
      }
    }
  }
}
</style>
