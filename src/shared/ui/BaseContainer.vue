<template>
  <div class="container">
    <slot />
  </div>
</template>

<style scoped lang="scss">
@import 'src/app/assets/styles/variables.scss';

.container {
  width: 100%;
  max-width: toRem($maxWidthContainer);
  padding: 0 $paddingContainer;
  margin: 0 auto;
}
</style>
