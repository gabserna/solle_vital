<script lang="ts">
import Vue from "vue";
import { BaseContainer, BaseAnimation } from "@/shared/ui";
import { isMobile } from "@/shared/lib";
import Coaster from "../images/coaster.png";
import MobileCoaster from "../images/coaster-mobile.png";

export default Vue.extend({
  components: {
    BaseContainer,
    BaseAnimation,
  },
  data() {
    return {
      Coaster,
      MobileCoaster,
      isMobile,
    };
  },
});
</script>

<template>
  <section class="coaster">
    <BaseContainer>
      <div class="coaster__content">
        <div class="coaster__header">
          <BaseAnimation :delay="200">
            <h2>Step off the stress roller coaster</h2>
          </BaseAnimation>
          <BaseAnimation :delay="400">
            <p>
              Stress is a daily and normal part of life, but if it begins to feel like a
              roller coaster that leaves you emotionally and physically exhausted on a
              daily basis, this may be a sign that your health is suffering negative
              consequences of stress and needs help. That’s where adaptogens come in.
              <strong>
                Adaptogens help stress feel less like a roller coaster and more like a
                bump in the road.
              </strong>
              They naturally <strong>promote a return to balance</strong> for both body
              and mind by helping the body modulate the neuroendocrine system responsible
              for stress hormones, increasing energy and stamina, and combating
              inflammation through their antioxidant properties.
            </p>
          </BaseAnimation>
        </div>
        <BaseAnimation :delay="600" v-if="!isMobile">
          <div class="coaster__image">
            <img :src="Coaster" alt="coaster" />
          </div>
        </BaseAnimation>
        <BaseAnimation :delay="600" v-if="isMobile">
          <div class="coaster__image">
            <img :src="MobileCoaster" alt="coaster" />
          </div>
        </BaseAnimation>
      </div>
    </BaseContainer>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.coaster {
  &__content {
    @include flexColumn();
    row-gap: toRem(73);
    max-width: toRem(1091);
    width: 100%;
    margin: 0 auto;
    text-align: center;

    @media (max-width: $mobile) {
      row-gap: toRem(38);
    }
  }

  &__header {
    @include flexColumn();
    row-gap: toRem(41);

    & p {
      line-height: 168.75%; /* 27/16 */
    }

    @media (max-width: $mobile) {
      row-gap: toRem(18);

      & p {
        font-size: toRem(12);
      }
    }
  }

  &__image {
    & img {
      width: 100%;
      aspect-ratio: 1091 / 376;

      @media (max-width: $mobile) {
        aspect-ratio: 359 / 400;
      }
    }
  }
}
</style>
