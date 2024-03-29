<script lang="ts">
import { defineComponent } from 'vue'; //defineComponent to verify isLoggedIn
import { BaseContainer, BaseAnimation, BaseButton } from '@/shared/ui';
import Wave from '../images/wave.png';
import VitalBox from '../images/vital-box3.png';
import { isTablet } from '@/shared/lib';
import { ref } from 'vue';

export default defineComponent({
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
      isLoggedIn: false, // to verify if user is logged in
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
});
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
                  Solle<strong>Vital®</strong> is a premium plant blend
                  consisting of three balanced ingredient groups:
                  <strong
                    >adaptogens, trace minerals, and our chlorophyll
                    blend.</strong
                  >
                </p>
              </BaseAnimation>
              <BaseAnimation :delay="600">
                <p>
                  These blends work together to provide essential nutrients that
                  strengthen core body systems such as the circulatory,
                  digestive, respiratory and immune systems, promote recovery,
                  and lift energy and mood.
                </p>
              </BaseAnimation>
            </div>
            <BaseAnimation :delay="700" v-if="isTablet">
              <div class="health__img">
                <img :src="VitalBox" alt="VitalBox" />
              </div>
            </BaseAnimation>

            <BaseAnimation :delay="800">
              <!-- .qty should appears only when logged in -->
              <div class="qty" v-if="isLoggedIn">
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
              </div>
            </BaseAnimation>

            <BaseAnimation :delay="800">
              <div class="qty__discover" v-if="isLoggedIn">
                <p>
                  Discover your custom product recommendations when you take our
                  quiz!
                </p>
                <a href="https://www.sollenaturals.com/take-our-quiz"
                  >Take the Quiz</a
                >
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
@import 'src/app/assets/styles/variables.scss';
.health {
  position: relative;
  padding-top: 0;

  @media (max-width: $xs) {
    h2 {
      text-align: start;
      font-size: 2rem;
    }
    p {
      font-size: toRem(14);
    }
  }

  &__wave {
    & img {
      width: 100%;
      aspect-ratio: 1604 / 164;
      object-fit: cover;
      object-position: top center;
    }
  }

  &__wrapper {
    position: relative;
    z-index: $zIndex_1;
    background-color: $white;
    padding: 0 5rem;

    @media (max-width: $xs) {
      padding: 1rem 0 0 0;
    }
  }

  &__content {
    display: grid;
    grid-template-columns: minmax(toRem(524), 1fr) 1fr;
    align-items: center;
    justify-content: space-between;
    gap: toRem(35);

    @media (max-width: $sm) {
      grid-template-columns: 1fr;
      justify-content: center;
      gap: toRem(12);
      max-width: toRem(610);
      margin: 0 auto;
      text-align: center;
      margin: 0 20vh;
    }

    @media (max-width: $xs) {
      padding: 0;
      width: 100%;
      margin: 0 auto;
    }
  }

  &__box {
    @include flexColumn();
    row-gap: toRem(24);

    @media (max-width: $mobile) {
      row-gap: toRem(8);
    }
  }

  &__subtitle {
    @include flexColumn();
    row-gap: toRem(24);
    line-height: 168.75%; /* 27/16 */

    @media (max-width: $mobile) {
      row-gap: toRem(10);
    }
    @media (max-width: $xs) {
      text-align: left;
    }
  }

  &__img {
    text-align: center;

    @media (max-width: $tablet) {
      margin-top: toRem(24);
    }

    & img {
      max-width: toRem(610);
      width: 100%;
      height: 80%;
      aspect-ratio: 610 / 532;
      object-fit: contain;
      object-position: center;

      @media (max-width: $xs) {
        z-index: -2;
        object-position: top;
        max-width: toRem(500);
        height: toRem(260);
        aspect-ratio: 580 / 532;
      }
    }
  }
}

.qty {
  @include flexColumn();
  row-gap: toRem(32);
  text-align: left;

  @media (max-width: $mobile) {
    row-gap: toRem(26);
  }

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

    @media (max-width: $mobileSmall) {
      font-size: toRem(10);

      & strong {
        font-size: toRem(12);
      }
    }
  }

  &__price {
    @include flexRow(center);
    column-gap: toRem(26);
  }

  &__switcher {
    @include flexRow(center);
    background-color: $parchment_cream;
    border-radius: toRem(30);
    width: fit-content;

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

      @media (max-width: $mobile) {
        width: toRem(24);
        height: toRem(24);
        font-size: toRem(8);
      }
    }
  }

  &__value {
    font-size: toRem(24);
    font-weight: 300;

    & b {
      font-weight: 400;
    }

    @media (max-width: $mobile) {
      font-size: toRem(14);
    }
  }

  &__box {
    @include flexRow(center);
    column-gap: toRem(12);

    @media (max-width: $xs) {
      padding: 0;
      margin: 0;
      column-gap: toRem(0);
    }
  }

  &__button {
    font-size: toRem(14);
    letter-spacing: em(0.35);
    font-weight: 400;
    padding: toRem(7.5) toRem(30);
    color: $mainColor;

    @media (max-width: $mobile) {
      font-size: toRem(12);
      padding: toRem(8.5) toRem(15);
    }
  }

  &__counter {
    @include flexRow(center);
    column-gap: toRem(2);
    border: toRem(1) solid $accent;
    border-radius: toRem(30);
    padding: toRem(4) toRem(9);
    font-size: toRem(14);

    @media (max-width: $mobile) {
      font-size: toRem(12);
    }

    & > button {
      @include flexRow(center, center);
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
      @include flexRow(center, center);
      text-align: center;
      width: toRem(14);
      height: toRem(25);
    }
  }

  &__discover {
    font-size: toRem(14);

    @media (max-width: $mobile) {
      font-size: toRem(10);
      line-height: 150%; /* 15/10 */
    }

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

@media (max-width: $xs) {
  // less then 600px
}

@media (min-width: $sm) and (max-width: $md) {
  // from 600px to 906px
}

@media (min-width: $md) and (max-width: $lg) {
  // from 906px to 1264px
}

@media (min-width: $lg) and (max-width: $xl) {
  // from 1264px to 1904px
}

@media (min-width: $xl) {
  // greater than 1904px
}
</style>
