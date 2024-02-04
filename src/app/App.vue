<script lang="ts">
import Vue from "vue";
import { MainHeader } from "@/widgets/Header";
import { MainFooter } from "@/widgets/Footer";
import {
  SectionPreview,
  SectionMain,
  SectionKey,
  SectionCoaster,
  SectionMinerals,
  SectionPlants,
  SectionComments,
  SectionMixing,
  SectionSeo,
} from "@/widgets/MainSections";
import { getCurrentLocale } from "./i18n/utils";
import { setLanguage } from "./i18n/hooks";

export default Vue.extend({
  components: {
    MainHeader,
    MainFooter,
    SectionPreview,
    SectionMain,
    SectionKey,
    SectionCoaster,
    SectionMinerals,
    SectionPlants,
    SectionComments,
    SectionMixing,
    SectionSeo,
  },
  mounted() {
    const currentLocale = getCurrentLocale();
    setLanguage(currentLocale);
  },
});
</script>

<template>
  <v-app>
    <MainHeader />
    <v-main>
      <SectionPreview />
      <SectionMain />
      <div class="app__wrapper">
        <SectionKey />
        <SectionCoaster />
        <SectionMinerals />
        <SectionPlants />
        <SectionComments />
        <SectionMixing />
        <SectionSeo />
      </div>
    </v-main>
    <MainFooter />
  </v-app>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";
.app {
  &__wrapper {
    position: relative;
    z-index: $zIndex_1;
    background-color: $white;
  }
}
</style>
