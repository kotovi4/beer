<template>
  <button type="button" :class="$style.button">Random beer!</button>
</template>

<script>
  export default {
    name: 'ButtonRandomBeer',
  }
</script>

<style module lang="scss">
@import '~@/styles/root.scss';

.button {
  width: 100%;
  margin-top: 50px;
  padding: 30px;
  color: var(--common);
  background-color: var(--red);
  border: none;
  border-radius: 5px;
  font-weight: 400;
  font-size: 35px;
  line-height: 130%;
  letter-spacing: 0.06em;

  &:hover {
    opacity: 0.7;
    transition: all 0.3s;
  }
}
</style>