<script lang="ts">
import { BaseContainer } from "@/shared/ui";

import Avatar from "../images/avatar.png";
import Border from "../images/border.png";
import Dots from "../images/dots.png";
import Product from "../images/product.png";

export default {
  components: {
    BaseContainer,
  },
  data() {
    return {
      Avatar,
      Border,
      Dots,
      Product,
    };
  },
};
</script>

<template>
  <v-container>

    <section class="seo">
      <!-- <BaseContainer> -->
        <div class="seo__wrap">
          <img class="seo__border" :src="Border" alt="Border" />
        <div class="seo__dots">
          <img :src="Dots" alt="Dots" />
        </div>
        <div class="seo__product">
          <img :src="Product" alt="Product" />
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
      <!-- </BaseContainer> -->
    </section>
  </v-container>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.seo {
  
  padding-bottom: 1rem;

  @media (max-width: $tablet) {
    padding-top: 0;
  }
  
  &__wrap {
    position: relative;
    max-width: toRem(1200);
    width: 100%;
    text-align: center;
    margin: 0 auto;
    transform: translate(10%, 0);
    
    @include adaptiveValue("height", 596, 496, 1300, 991, 1);
    
    @media (max-width: $tablet) {
      @include flexColumn(center, center);
      height: auto;
      margin: 0 auto;
    }

      @media (max-width: $xs) {
      padding: 0;
      margin: 0;
      width: 80%;
      height: auto;
    }
  }
  
  &__product {
    position: absolute;
    left: 0;
    top: 50%;
    transform: translate(-45%, -50%);
    
    & img {
      @include adaptiveValue("width", 590, 490, 1300, 991, 1);
    }
    
    @media (max-width: $tablet) {
      position: relative;
      top: auto;
      transform: translate(0);
      padding-right: 3%;
      
      & img {
        width: toRem(300);
      }
    }
  }
  
  &__content {
    position: relative;
    @include flexColumn(center, center);
    row-gap: toRem(10);
    height: 100%;
    padding: toRem(102) toRem(83) toRem(38);
    z-index: $zIndex_1;
    max-width: toRem(724);
    transform: translate(0, 0);
    margin: 0 auto;
    
    @media (max-width: $pc) {
      row-gap: toRem(24);
    }
    
    @media (max-width: $tablet) {
      padding: 0;
    } 
    @media (max-width: $xs) {
      width: 100%;
      margin: 0;
      left: 1rem;
      row-gap: toRem(18);
    }
  }
  
  &__border {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    object-fit: contain;
    
    @media (max-width: $tablet) {
      display: none;
    }
  }
  
  &__dots {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: $white;
    width: toRem(276);
    
    @media (max-width: $tablet) {
      display: none;
    }
  }
  
  &__text {
    font-size: toRem(22);
    line-height: 150%; /* 33/22 */
    
    @media (max-width: $pc) {
      font-size: toRem(20);
    }
    
    @media (max-width: $mobile) {
      font-size: toRem(14);
    }
  }
  
  &__info {


    & p {
      & strong {
        display: block;
        font-size: toRem(20);
      }
    }
    
    @media (max-width: $pc) {
      & img {
        width: toRem(142);
      }
    }
    
    @media (max-width: $mobile) {
      & img {
        width: toRem(92);
      }
      
      & p {
        font-size: toRem(10);
        
        & strong {
          font-size: toRem(12);
        }
      }
    }
  }
}
</style>
