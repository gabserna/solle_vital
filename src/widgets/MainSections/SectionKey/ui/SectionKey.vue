<script lang="ts">
import { defineComponent, ref } from "vue";
import { BaseContainer, TriangleIcon } from "@/shared/ui";
import Wave from "../images/wave.png";

import Core from "../images/core.png";
import Body from "../images/body.png";
import Mood from "../images/mood.png";
import Hand from "../images/hand.png";

import MoodIcon from "../images/mood-icon.png";
import StaminaIcon from "../images/stamina-icon.png";
import DetoxIcon from "../images/detox-icon.png";
import RecoveryIcon from "../images/recovery-icon.png";
import AlkalizingIcon from "../images/alkalizing-icon.png";

interface BenefitType {
  title: string;
  icon: string;
  text: string;
}

const benefits: BenefitType[] = [
  {
    title: "Mood",
    icon: MoodIcon,
    text:
      "Helps the body to balance and elevate your mood while promoting a healthy stress response",
  },
  {
    title: "Stamina",
    icon: StaminaIcon,
    text:
      "Adaptogens help the body maintain energy levels throughout the day for fewer crashes",
  },
  {
    title: "Detoxing",
    icon: DetoxIcon,
    text:
      "Chlorophyll naturally aids the body in eliminating toxins that build up over time",
  },
  {
    title: "Recovery",
    icon: RecoveryIcon,
    text: "Trace minerals restore necessary minerals and help to oxygenate the blood",
  },
  {
    title: "Alkalizing",
    icon: AlkalizingIcon,
    text:
      "Chlorophyll helps balance pH levels in the body, which reduces acidity and promotes a feeling of overall wellness",
  },
];

export default defineComponent({
  components: {
    BaseContainer,
    TriangleIcon,
  },
  setup() {
    const activeBenefit = ref<BenefitType>(benefits[0]);
    const setActiveBenefit = (benefit: BenefitType) => (activeBenefit.value = benefit);

    return {
      Wave,
      Hand,
      cards: [{ img: Core }, { img: Body, withTransform: true }, { img: Mood }],
      benefits,
      activeBenefit,
      setActiveBenefit,
    };
  },
});
</script>

<template>
  <section class="preview">
    <div class="preview__image">
      <img :src="Wave" alt="wave" />
    </div>
    <div class="preview__wrapper">
      <BaseContainer>
        <div class="preview__content">
          <div class="preview__cards">
            <div
              v-for="(card, index) in cards"
              :key="index"
              class="preview__card"
              :class="card.withTransform && 'transform'"
            >
              <img :src="card.img" alt="Card" />
            </div>
          </div>
          <div class="display">
            <div class="display__wrapper">
              <div class="display__header"><h2>Key benefits</h2></div>
              <div class="display__hand">
                <img :src="Hand" alt="hand" />
              </div>
              <div class="display__content">
                <ul class="display__list">
                  <li
                    v-for="(benefit, index) in benefits"
                    :key="index"
                    class="display__item"
                  >
                    <button
                      @click="() => setActiveBenefit(benefit)"
                      :class="benefit.title === activeBenefit.title && 'active'"
                      type="button"
                    >
                      {{ benefit.title }}
                    </button>
                    <TriangleIcon
                      class="display__triangle"
                      v-if="benefit.title === activeBenefit.title"
                    />
                  </li>
                </ul>
                <div class="display__card">
                  <img :src="activeBenefit.icon" alt="icon" />
                  <p>{{ activeBenefit.text }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </BaseContainer>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.preview {
  padding: 0;
  position: relative;

  &__image {
    & img {
      width: 100%;
      aspect-ratio: 1532 / 84;
      object-fit: cover;
      object-position: top center;
    }
  }

  &__wrapper {
    position: relative;
    padding-top: toRem(44);

    &::before {
      content: "";
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 60%;
      background-color: $parchment_cream;
      z-index: $zIndex_1;
    }
  }

  &__content {
    position: relative;
    z-index: $zIndex_1;
  }

  &__cards {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: toRem(24);
    max-width: toRem(1100);
    margin: 0 auto;
    padding: 0 toRem(88);

    @media (max-width: em(600)) {
      padding: 0;
      max-width: toRem(331);
    }
  }

  &__card {
    text-align: center;

    &.transform {
      transform: translateY(toRem(-30));
    }

    & img {
      @media (max-width: $tablet) {
        width: toRem(100);
      }
      @media (max-width: $mobile) {
        width: toRem(65);
      }
    }
  }
}
.display {
  position: relative;
  max-width: toRem(1100);
  margin: 0 auto;
  border-radius: toRem(10);
  margin-top: toRem(80);
  background: linear-gradient(
    359.49deg,
    #c0df16 0.37%,
    rgba(192, 223, 22, 0.546875) 21.54%,
    #dfeda6 56.13%
  );

  @media (max-width: $tablet) {
    margin-bottom: toRem(240);
  }

  @media (max-width: em(600)) {
    margin-bottom: toRem(120);
  }

  @media (max-width: $mobile) {
    margin-top: toRem(50);
  }

  &__wrapper {
    margin: 0 auto;

    @media (max-width: $tablet) {
      max-width: toRem(431);
      padding-left: toRem(36);
    }

    @media (max-width: em(600)) {
      max-width: toRem(331);
    }
  }

  &__header {
    position: relative;
    text-align: center;
    padding: toRem(60) 0 toRem(15);

    &::before {
      content: "";
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translateX(-50%);
      max-width: toRem(314);
      width: 100%;
      height: toRem(3);
      background-color: $white;
      border-radius: toRem(8);
    }

    @media (max-width: em(600)) {
      padding-top: toRem(32);
      padding-bottom: toRem(8);
      text-align: left;
      width: fit-content;
    }
  }

  &__hand {
    position: absolute;
    left: 0;
    bottom: 0;

    & img {
      @include adaptiveValue("width", 450, 300, 1200, 991, 1);
    }

    @media (max-width: $tablet) {
      bottom: 0;
      left: 50%;
      transform: translate(-15%, -25%);

      & img {
        width: toRem(342);
      }
    }

    @media (max-width: em(600)) {
      transform: translate(-20%, -18%);

      & img {
        width: toRem(222);
      }
    }

    @media (max-width: em(360)) {
      transform: translate(-25%, -25%);

      & img {
        width: toRem(180);
      }
    }
  }

  &__content {
    @include flexRow(center, space-between);
    column-gap: toRem(38);
    padding: toRem(60) toRem(72) toRem(82) toRem(450);

    @include adaptiveValue("padding-left", 450, 300, 1200, 991, 1);

    @media (max-width: $tablet) {
      padding: toRem(60) 0 toRem(260);
    }

    @media (max-width: em(600)) {
      padding-top: toRem(36);
      padding-bottom: toRem(130);
    }
  }

  &__list {
    position: relative;
    @include flexColumn(flex-start);
    row-gap: toRem(28);

    @media (max-width: $tablet) {
      row-gap: toRem(20);
      flex-direction: column-reverse;
    }
  }

  &__item {
    position: relative;
    @include flexRow(center);
    width: 100%;
    min-width: toRem(158);

    @media (max-width: $tablet) {
      display: contents;
    }

    & button {
      font-size: toRem(32);
      line-height: 106.25%; /* 34/32 */
      font-weight: 300;
      transition: opacity $transition;

      @media (any-hover: hover) {
        &:hover:not(.active) {
          opacity: 0.8;
        }
      }

      &.active {
        font-weight: 600;
      }

      @media (max-width: $mobile) {
        font-size: toRem(28);
      }

      @media (max-width: em(600)) {
        font-size: toRem(16);
      }
    }
  }

  &__triangle {
    position: absolute;
    left: 100%;
    transform: translateX(50%);
    color: #bdd631;

    @media (max-width: $tablet) {
      bottom: toRem(-145);
      left: toRem(23);
      transform: rotate(90deg);
      z-index: $zIndex_5;
    }

    @media (max-width: em(600)) {
      width: toRem(26);
      height: toRem(24);
      bottom: toRem(-78);
      left: toRem(43);
    }
  }

  &__card {
    max-width: toRem(377);
    flex: 0 0 toRem(377);
    min-height: toRem(361);
    width: 100%;
    @include flexColumn(center);
    row-gap: toRem(12);
    text-align: center;
    background-color: $white;
    border-radius: toRem(10);
    padding: toRem(26) toRem(32) toRem(26);
    box-shadow: toRem(2) toRem(4) toRem(4) 0 #bcbab180;

    & p {
      font-size: toRem(24);
      line-height: 133.333333%; /* 32/24 */
    }

    @media (max-width: $tablet) {
      position: absolute;
      bottom: 0;
      left: 50%;
      transform: translate(-50%, 65%);
      border-radius: toRem(20);
      z-index: $zIndex_1;
    }

    @media (max-width: em(600)) {
      padding: toRem(16) toRem(8);
      row-gap: toRem(8);
      max-width: toRem(209);
      min-height: toRem(176);

      & img {
        width: toRem(63);
      }
      & p {
        font-size: toRem(12);
      }
    }
  }
}
</style>
