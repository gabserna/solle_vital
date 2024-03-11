<script lang="ts">
import Vue from 'vue';
import { BaseContainer, BaseAnimation } from '@/shared/ui';
import { isMobile } from '@/shared/lib';

import Wave from '../images/wave.png';
import BottomWave from '../images/wave-bottom.png';
import Broccoli from '../images/broccoli.png';

export default Vue.extend({
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      Wave,
      BottomWave,
      Broccoli,
      isMobile,
    };
  },
});
</script>

<template>
  <section class="coaster">
    <div class="coaster__image">
      <img :src="Wave" alt="wave" />
    </div>
    <div class="coaster__wrapper">
      <BaseContainer>
        <div class="coaster__content">
          <div class="coaster__header">
            <BaseAnimation :delay="200">
              <h2>Why include trace minerals?</h2>
              <!-- <h2>Step off the stress roller coaster</h2> -->
            </BaseAnimation>
          </div>
          <div class="coaster__body">
            <div class="coaster__info">
              <BaseAnimation :delay="400">
                <p>
                  Trace minerals are the definition of small but mighty.
                  <strong>
                    Almost all bodily process require trace minerals in order to
                    function, yet we cannot produce them on our own.
                  </strong>
                  If the body does not get enough of these critical nutrients,
                  there is an increased risk of health issues including high
                  blood pressure, pain, depression, poor digestion and more.
                </p>
              </BaseAnimation>
              <BaseAnimation :delay="600">
                <p>
                  So where do these minerals come from? The soil that our food
                  is grown in! The problem with this is that most soil is not
                  what it used to be, leading to significant mineral depletion
                  in our food.
                </p>
              </BaseAnimation>
              <BaseAnimation :delay="800">
                <p>
                  To the right you’ll find an example of this, courtesy of a
                  study conducted by the Kushi Institute that compares the
                  mineral concentration in broccoli in 1975 and now.
                </p>
              </BaseAnimation>
              <BaseAnimation :delay="1000">
                <p>
                  To help combat this, we included four herbs rich in trace
                  minerals in the Solle<strong>Vital</strong> formula - burdock,
                  avena sativa, dandelion and nettle.
                </p>
              </BaseAnimation>
            </div>
            <BaseAnimation variant="opacity" :delay="600" v-if="!isMobile">
              <div class="coaster__img">
                <img :src="Broccoli" alt="Broccoli" />
              </div>
            </BaseAnimation>
            <BaseAnimation variant="slideDown" :delay="1200" v-if="isMobile">
              <div class="coaster__img">
                <img :src="Broccoli" alt="Broccoli" />
              </div>
            </BaseAnimation>
          </div>
        </div>
      </BaseContainer>
    </div>
    <div class="coaster__wave">
      <img :src="BottomWave" alt="wave" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import 'src/app/assets/styles/variables.scss';

.coaster {
  position: relative;
  overflow: hidden;

  @media (max-width: $xs) {
    h2 {
      font-size: 2rem;
    }

    p {
      font-size: toRem(14);
    }
  }

  &__image {
    & img {
      width: 100%;
      aspect-ratio: 1518 / 103;
      object-fit: cover;
      object-position: top center;
    }
  }

  &__wave {
    & img {
      width: 100%;
      aspect-ratio: 1124 / 124;
      object-fit: cover;
      object-position: bottom center;
    }
  }

  &__wrapper {
    position: relative;
    background-color: #eceade;
  }

  &__content {
    padding-top: toRem(58);
  }

  &__header {
    text-align: center;
  }

  &__body {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: toRem(24);
    align-items: center;
    justify-content: space-between;
    margin-top: toRem(58);

    @media (max-width: $mobile) {
      grid-template-columns: 1fr;
      row-gap: toRem(38);
      margin-top: toRem(21);
    }
  }

  &__info {
    @include flexColumn();
    row-gap: toRem(20);

    @media (max-width: $mobile) {
      text-align: center;
      font-size: toRem(14);
    }
  }

  &__img {
    & img {
      width: 100%;
      aspect-ratio: 591 / 421;
    }

    @media (max-width: $xs) {
      width: toRem(500);
      aspect-ratio: 591 / 421;
      transform: translateX(0%);
    }
  }
}
</style>
