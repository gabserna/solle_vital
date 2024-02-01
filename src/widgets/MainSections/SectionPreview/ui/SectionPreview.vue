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
  <section class="preview">
    <div class="preview__video">
      <DesctopVideo v-if="!isMobile" />
      <MobileVideo v-if="isMobile" />
    </div>
  </section>
</template>

<style lang="scss" scoped>
@import "src/app/assets/styles/variables.scss";

.preview {
  position: relative;
  @include flexColumn(center, center);
  height: min(100vh, toRem(1080));
  padding-top: 0;

  &__video {
    position: fixed;
    left: 0;
    top: $header_height;
    width: 100%;
    height: min(100vh, toRem(1080));

    & video {
      position: absolute;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center;
    }
  }
}
</style>
