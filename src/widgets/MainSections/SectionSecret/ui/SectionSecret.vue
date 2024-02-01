<script lang="ts">
import { BaseContainer } from "@/shared/ui";

import Avatar from "../images/avatar.png";
import Border from "../images/border.png";
import Dots from "../images/dots.png";

export default {
  components: {
    BaseContainer,
  },
  data() {
    return {
      Avatar,
      Border,
      Dots,
    };
  },
};
</script>

<template>
  <section class="seo">
    <BaseContainer>
      <div class="seo__wrap">
        <img class="seo__border" :src="Border" alt="Border" />
        <div class="seo__dots">
          <img :src="Dots" alt="Dots" />
        </div>
        <div class="seo__content">
          <p class="seo__text">
            Solle<b>Vital</b> is the first of Solle’s four signature drinks, and for good
            reason is at the center of our philosophy of daily nourishment to both body
            and mind. Its unique blend of concentrated adaptogens, key plant minerals, and
            select chlorophylls provide therapeutic balance and enable greater results for
            all nutrition programs.
          </p>
          <div class="seo__info">
            <img :src="Avatar" alt="Greg Halliday" />
            <p><strong>Greg Halliday</strong> Founder/CEO</p>
          </div>
        </div>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.seo {
  &__wrap {
    position: relative;
    max-width: toRem(1072);
    margin: 0 auto;
    width: 100%;
    height: toRem(540);
    text-align: center;
  }

  &__content {
    position: relative;
    @include flexColumn(center, center);
    row-gap: toRem(40);
    height: 100%;
    padding: toRem(102) toRem(83) toRem(38);
    z-index: $zIndex_1;
  }

  &__border {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    object-fit: contain;
  }

  &__dots {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: $white;
    width: toRem(276);
  }

  &__text {
    font-size: toRem(22);
  }

  &__info {
    & p {
      & strong {
        display: block;
        font-size: toRem(20);
      }
    }
  }
}
</style>
