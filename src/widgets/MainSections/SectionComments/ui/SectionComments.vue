<script lang="ts">
import Vue from 'vue';
import Swiper from 'swiper';
import { Navigation, Autoplay, Pagination } from 'swiper/modules';
import { BaseContainer, BaseRating } from '@/shared/ui';
import Background from '../images/Background.png';
import { isMobile } from '@/shared/lib';

interface IComment {
  text: string;
  name: string;
  status: string;
}

export default Vue.extend({
  components: {
    BaseContainer,
    BaseRating,
  },
  data() {
    return {
      isMobile,
      Background,
      COMMENTS: [
        {
          text: '“I love drinking my green drink every morning! I immediately feel better when I’m done. Solle vital has replaced my daily vitamins!!”',
          name: 'Shannon M.',
          status: 'Verified Customer',
        },
        {
          text: '“Balances my body, gives me energy, keeps me healthy and tastes so good! Can’t go a day without my Vital!!”',
          name: 'Jason S.',
          status: 'Verified Customer',
        },
        {
          text: '“I have felt a lot more energy since using Solle vital. I have also suffered from depression and anxiety and this product has helped me feel more clarity of mind.”',
          name: 'Brittney B.',
          status: 'Verified Customer',
        },
        {
          text: '“This drink has helped my son... immensely he can focus now, better mood and doesnt get in trouble at school as much”',
          name: 'Nikki Z.',
          status: 'Verified Customer',
        },
        {
          text: '“Vital has helped with my overall wellbeing, my sinuses are better and my stress is less”',
          name: 'Alicia K.',
          status: 'Verified Customer',
        },

        {
          text: '“I feel so much better since I started Vital. I have more energy & my anxiety is less.”',
          name: 'Dawn K.',
          status: 'Verified Customer',
        },
        {
          text: '“Sollevital has been a life savor for me. I am a non Hopkins lymphoma cancer patient that recovered and sollevital has been so helpful in giving me the needed energy. Go Sollenaturals!”',
          name: 'Dolores V.',
          status: 'Verified Customer',
        },
        {
          text: '“This is so a great product that gives me energy without (a crash) and it’s a great breakfast before my meetings”',
          name: 'Carmen V.',
          status: 'Verified Customer',
        },
        {
          text: '“Its an absolute start to my morning! Adding my other products to my arsenal has helped my mental health and boosted my immunity. I cant imagine starting my day without it”',
          name: 'Connie H.',
          status: 'Verified Customer',
        },
      ] as IComment[],
      swiperOptions: {
        modules: [Navigation, Autoplay, Pagination],
        loop: true,
        speed: 1000,
        slidesPerView: 1,
        spaceBetween: 24,
        autoplay: {
          delay: 10000,
          disableOnInteraction: true,
        },
        navigation: {
          nextEl: '.swiper-button-next',
          prevEl: '.swiper-button-prev',
        },

        pagination: {
          el: '.swiper-pagination',
          clickable: true,
          renderBullet: function (index: number, className: string) {
            return `<span class="${className}"></span>`;
          },
        },

        breakpoints: {
          767: {
            slidesPerView: 3,
            spaceBetween: 24,
          },
          991: {
            slidesPerView: 3,
            spaceBetween: 30,
          },
        },
      },
    };
  },
  // mounted() {
  //   new Swiper(this.$refs.swiper, this.swiperOptions);
  // },

  mounted() {
    if (this.$refs.swiper) {
      new Swiper(this.$refs.swiper as HTMLElement, this.swiperOptions);
    }
  },
});
</script>

<template>
  <section class="comments">
    <div class="comments__wrapper">
      <BaseContainer>
        <v-row no-gutters class="comments__header">
          <v-col>
            <h2>What people are saying</h2>
          </v-col>
        </v-row>
        <div class="comments__content">
          <div class="comments__swiper swiper" ref="swiper">
            <div class="swiper-wrapper">
              <div
                class="swiper-slide"
                v-for="(comment, index) in COMMENTS"
                :key="index"
              >
                <div class="comment" outlined>
                  <p class="comment__text">{{ comment.text }}</p>
                  <div class="comment__block">
                    <p class="comment__name">{{ comment.name }}</p>
                    <div class="comment__status">{{ comment.status }}</div>
                  </div>
                </div>
              </div>

              <div class="swiper-pagination" ref="pagination"></div>

            </div>
          </div>
          <button class="swiper-button-prev">
            <svg
              width="31"
              height="52"
              viewBox="0 0 31 52"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M27.4688 48.9766L4.23695 26.2299L26.9836 2.99825"
                stroke="currentColor"
                stroke-width="6"
                stroke-linecap="round"
              />
            </svg>
          </button>
          <button class="swiper-button-next">
            <svg
              width="31"
              height="52"
              viewBox="0 0 31 52"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M27.4688 48.9766L4.23695 26.2299L26.9836 2.99825"
                stroke="currentColor"
                stroke-width="6"
                stroke-linecap="round"
              />
            </svg>
          </button>
        </div>
      </BaseContainer>
      <div class="comments__bg">
        <img :src="Background" alt="background" />
      </div>
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import 'src/app/assets/styles/variables.scss';

.comments {
  position: relative;
  overflow: hidden;

  &__wrapper {
    background-color: #dfeda6;
    position: relative;
    padding: toRem(124) 0;
    overflow: hidden;

    @media (max-width: $mobile) {
      padding: toRem(45) 0;
    }

    @media (max-width: $xs) {
    // padding-bottom: toRem(150);

    h2 {
      font-size: 2rem;
      margin: 0 auto;
      width: 70%;
      text-align: center;
    }
    p {
      font-size: toRem(14);
    }
   
  }
  }

  &__header {
    position: relative;
    text-align: center;
    z-index: $zIndex_1;
    
    @media (max-width: $mobile) {
      max-width: toRem(472);
      margin: 0 auto;
    }
  }
  
  &__content {
    position: relative;
    margin-top: toRem(80);
    
    @media (max-width: $tablet) {
      margin: toRem(30);
      font-size: 2rem;
    }
  }

  &__swiper {
    padding: toRem(8) 0;
    @media (max-width: em($maxWidthContainer)) {
      margin: 0 $paddingContainerMinus;
      padding: toRem(4) $paddingContainer;
    }
  }

  &__bg {
    position: absolute;
    right: 0;
    bottom: -10%;

    @media (max-width: $mobile) {
      right: auto;
      left: 0;
      bottom: 0;

      & img {
        transform: scale(-1, 1);
        width: toRem(164);
        max-height: toRem(383);
        object-fit: contain;
        object-position: right;
      }
    }

    @media (max-width: $mobileSmall) {
      & img {
        max-height: toRem(333);
      }
    }
  }
}
.comment {
  border: none;
  position: relative;
  @include flexColumn(center, center);
  text-align: center;
  row-gap: toRem(15);
  background-color: $white;
  border-radius: toRem(15) toRem(15) toRem(15) 0;
  box-shadow: 2px 4px 4px 0px #bcbab180;
  height: toRem(303);
  overflow-y: auto;
  padding: toRem(24) toRem(48);
  @include adaptiveValue('height', 303, 350, 1100, 767, 1);

  @media (max-width: $tablet) {
    padding: toRem(24) toRem(14);
  }

  @media (max-width: $xs) {
    height: toRem(200);
    max-width: toRem(400);
    margin: 0 auto;
  }

  &__text {
    font-size: toRem(18);

    @media (max-width: $tablet) {
      font-size: toRem(16);
    }

    @media (max-width: $mobile) {
      font-size: toRem(12);
      line-height: 150%; /* 18/12 */
    }
  }

  &__name {
    font-weight: 500;
    font-size: toRem(12);
    line-height: 150%; /* 18/12 */

    @media (max-width: $mobile) {
      font-size: toRem(10);
    }
  }

  &__status {
    font-size: toRem(12);
    line-height: 150%; /* 18/12 */

    @media (max-width: $mobile) {
      font-size: toRem(8);
    }
  }
}

.swiper-button-prev,
.swiper-button-next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  display: block;
  color: $white;
  margin: 0 toRem(24);
  z-index: $zIndex_1;
  transition: opacity $transition;

  @media (any-hover: hover) {
    &:hover {
      opacity: 0.8;
    }
  }

  @media (max-width: em($maxWidthContainer)) {
    display: none;
  }
}

.swiper-button-prev {
  right: 100%;
}
.swiper-button-next {
  left: 100%;

  & svg {
    transform: scale(-1, 1);
  }
}
</style>
