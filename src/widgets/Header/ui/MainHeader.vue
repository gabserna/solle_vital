<script lang="ts">
import { BaseContainer, BaseLogo, ProfileIcon, CartIcon } from "@/shared/ui";
import { LanguageSelector } from "@/features/LanguageSelector";
import { isMobile } from "@/shared/lib";
import { useTranslation } from "@/app/i18n/hooks";

export default {
  name: "MainHeader",
  components: {
    BaseContainer,
    BaseLogo,
    LanguageSelector,
    ProfileIcon,
    CartIcon,
  },
  data() {
    return {
      isMobile,
      t: useTranslation("Header"),
    };
  },
};
</script>

<template>
  <header class="header">
    <BaseContainer>
      <v-row justify="space-between" align="center" no-gutters>
        <div class="d-flex">
          <BaseLogo />
        </div>
        <div class="d-flex justify-end">
          <div class="header__box">
            <a
              class="header__link header__link-profile"
              href="https://www.sollenaturals.com/login"
            >
              <span v-if="!isMobile">login</span>
              <ProfileIcon />
            </a>
            <LanguageSelector />
            <a
              class="header__link header__link-cart"
              href="https://www.sollenaturals.com/cart"
            >
              <CartIcon />
            </a>
          </div>
        </div>
      </v-row>
    </BaseContainer>
  </header>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.header {
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  background-color: $white;
  padding: toRem(5) 0;
  box-shadow: $box_shadow;
  z-index: $zIndex_50;

  &__box {
    @include flexRow(center);
    column-gap: toRem(30);

    @media (max-width: $mobile) {
      column-gap: toRem(20);
    }
  }

  &__link {
    @include flexRow(center);
    column-gap: toRem(15);
    transition: opacity $transition;

    @media (any-hover: hover) {
      &:hover {
        opacity: 0.8;
      }
    }

    @media (max-width: $mobile) {
      &-profile {
        & svg {
          width: toRem(27);
          height: toRem(27);
        }
      }

      &-cart {
        width: toRem(32);
        height: toRem(26);
      }
    }
  }
}
</style>
