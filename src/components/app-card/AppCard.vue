<template>
  <div :class="$style.container">
    <user-card />
    <beer-card />
  </div>
</template>

<script>
import UserCard from "../user-card/UserCard.vue";
import BeerCard from "../beer-card/BeerCard.vue";

export default {
  name: "AppCard",
  components: {
    UserCard,
    BeerCard,
  }
};
</script>

<style module lang="scss">
@import "~@/styles/mixin.scss";

.container {
  display: flex;
  justify-content: center;
  margin: 0 auto;
  padding: 0 35px;
  max-width: 1440px;

  @include screen-l {
    flex-wrap: wrap;
    padding: 0;
  }
}
</style>
