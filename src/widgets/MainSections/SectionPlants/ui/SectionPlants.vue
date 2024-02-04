<script lang="ts">
import { defineComponent } from "vue";
import { BaseContainer, BaseAnimation } from "@/shared/ui";

import ChloroPhyll from "../images/ChloroPhyll.png";
import Greens from "../images/Greens.png";

export default defineComponent({
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      ChloroPhyll,
      Greens,
    };
  },
});
</script>

<template>
  <section class="chlorophyll">
    <BaseContainer>
      <div class="chlorophyll__content">
        <div class="chlorophyll__header">
          <BaseAnimation :delay="200">
            <h2>Chlorophyll</h2>
          </BaseAnimation>
          <BaseAnimation :delay="400">
            <p>it’s not just for plants</p>
          </BaseAnimation>
        </div>
        <BaseAnimation :delay="600">
          <div class="chlorophyll__body">
            <div class="phyll">
              <div class="phyll__wrap">
                <div class="phyll__image">
                  <img :src="ChloroPhyll" alt="ChloroPhyll" />
                </div>
                <ul class="phyll__list">
                  <li>Accelerates wound healing</li>
                  <li>Eliminates bad breath</li>
                  <li>Promotes digestion</li>
                  <li>Balances pH levels</li>
                  <li>Detoxifies the body</li>
                  <li>Helps restore red blood cells</li>
                </ul>
              </div>
              <p class="phyll__text">
                Chlorophyll may be famous for giving plants their green color, but its
                purposes do not end there. It's also packed with hundreds of nutrients
                essential for human health and has dozens of positive effects on overall
                well-being. For example chlorophyll helps calm the nerves, allowing you to
                remain focused during stressful times. It also helps oxygen travel through
                the bloodstream, giving you more energy and increased brain function.
              </p>
            </div>
            <div class="greens">
              <div class="greens__block">
                <p class="greens__title">4 sources of chlorophyll</p>
                <ul class="greens__list">
                  <li><strong>Mulberry</strong> Fruit Extract</li>
                  <li><strong>Alfalfa</strong> Extract</li>
                  <li><strong>Spinach</strong> Leaf Powder</li>
                  <li><strong>Nettle</strong> Whole Herb Powder</li>
                </ul>
              </div>
              <div class="greens__img">
                <img :src="Greens" alt="Greens" />
              </div>
            </div>
          </div>
        </BaseAnimation>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.chlorophyll {
  overflow-x: hidden;

  @media (max-width: $mobile) {
    overflow: hidden;
    padding-bottom: toRem(150);
  }

  &__content {
    @include flexColumn();
    row-gap: toRem(90);

    @media (max-width: $mobileSmall) {
      row-gap: toRem(60);
    }
  }

  &__header {
    position: relative;
    @include flexColumn();
    row-gap: toRem(5);
    text-align: center;
    z-index: $zIndex_1;

    & p {
      @include adaptiveValue("font-size", 36, 16, 991, 375, 1);
      font-weight: 300;
    }
  }

  &__body {
    display: grid;
    grid-template-columns: 1.1fr 1fr;
    min-height: toRem(635);

    @media (max-width: $mobile) {
      grid-template-columns: 1fr;
      row-gap: toRem(38);
      max-width: toRem(472);
      margin: 0 auto;
      min-height: auto;
    }
  }
}

.phyll {
  @include flexColumn();
  row-gap: toRem(36);
  padding-right: toRem(40);
  margin-right: toRem(40);
  border-right: toRem(1) solid $mainColor;

  @media (max-width: $tablet) {
    padding-right: toRem(20);
    margin-right: toRem(20);
  }

  @media (max-width: $mobile) {
    padding-right: 0;
    margin-right: 0;
    border-right: none;
    row-gap: toRem(21);
  }

  &__wrap {
    position: relative;
  }

  &__image {
    position: absolute;
    top: -23%;

    @include adaptiveValue("left", -70, -384, 1444, 767, 1);

    @media (max-width: $mobile) {
      @include adaptiveValue("left", -50, -180, 500, 375, 1);

      & img {
        width: toRem(449);
      }
    }
  }

  &__list {
    position: relative;
    @include flexColumn(flex-end);
    row-gap: toRem(36);
    text-align: right;
    // padding-left: toRem(350);
    z-index: $zIndex_1;

    @media (max-width: $mobile) {
      row-gap: toRem(21);
    }

    & li {
      font-weight: 500;
      font-size: toRem(20);

      &:nth-child(1) {
        padding-right: toRem(12);
      }
      &:nth-child(2) {
        padding-right: toRem(6);
      }
      &:nth-child(6) {
        padding-right: toRem(12);
      }
      &:nth-child(5) {
        padding-right: toRem(6);
      }

      @media (max-width: $mobile) {
        font-size: toRem(14);
      }
    }
  }

  &__text {
    @media (max-width: $mobile) {
      font-size: toRem(12);
    }
  }
}

.greens {
  position: relative;

  &__block {
    @include flexColumn();
    row-gap: toRem(46);
    max-width: toRem(206);
    position: relative;
    z-index: $zIndex_1;

    @media (max-width: $mobile) {
      row-gap: toRem(34);
    }
  }

  &__title {
    font-size: toRem(30);
    font-weight: 600;
    line-height: 150%; /* 45/30 */

    @media (max-width: $mobile) {
      font-size: toRem(20);
    }
  }

  &__list {
    @include flexColumn();
    row-gap: toRem(35);

    @media (max-width: $mobile) {
      row-gap: toRem(57);
    }

    & li {
      line-height: 150%;

      & strong {
        display: block;
        font-size: toRem(24);
      }

      @media (max-width: $mobile) {
        font-size: toRem(12);

        & strong {
          font-size: toRem(16);
        }
      }
    }
  }

  &__img {
    position: absolute;
    top: -20%;

    @include adaptiveValue("right", -100, -224, 1444, 991, 1);

    @media (max-width: $tablet) {
      top: -15%;

      & img {
        width: toRem(558);
      }
    }

    @media (max-width: $mobile) {
      top: 0;
      @include adaptiveValue("right", -150, -200, 500, 375, 1);

      & img {
        width: toRem(472);
      }
    }
  }
}
</style>
