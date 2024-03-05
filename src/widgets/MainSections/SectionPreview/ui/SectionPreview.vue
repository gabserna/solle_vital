<script lang="ts">
import { defineComponent } from "vue";
import { BaseContainer, BaseAnimation, BaseButton } from "@/shared/ui";
import { isMobile } from "@/shared/lib";
import DesctopVideo from "./DesctopVideo.vue";
import MobileVideo from "./MobileVideo.vue";

export default defineComponent({
  components: {
    BaseContainer,
    BaseAnimation,
    BaseButton,
    DesctopVideo,
    MobileVideo,
  },
  data() {
    return {
      isMobile,
    };
  }
});
</script>

<template>
  <v-container>
    <v-row>
      <section class="preview">
        <div class="preview__video">
          <DesctopVideo v-if="!isMobile" />
          <MobileVideo v-if="isMobile" />
        </div>
      </section>
    </v-row>
  </v-container>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.preview {
  position: relative;
  @include flexColumn(center, center);
  height: min(50vh, toRem(1080)); //changed to 50vh from 100vh
  padding-top: 0;

  &__video {
    position: fixed;
    left: 0;
    top: $header_height;
    width: 100%;
    height: min(80vh, toRem(1080));  //changed to 80vh from 100vh

    & video {
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 80%;  //changed to 80% from 100%
      object-fit: cover;
      object-position: center;
    }
  }
}
</style>
