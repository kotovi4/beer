<template>
  <section :class="$style.beer">
    <p>We recommended you:</p>
    <ul>
      <li><b>Brand:</b> {{ brand }}</li>
      <li><b>Name beer:</b> {{ name }}</li>
      <li><b>Malts:</b> {{ style }}</li>
      <li><b>Alc:</b> {{ alcohol }}</li>
      <li><b>Blg:</b> {{ blg }}</li>
    </ul>
    <button-random-beer @click="randomBeer" />
  </section>
</template>

<script>
import axios from 'axios'
import ButtonRandomBeer from '../button-random-beer/ButtonRandomBeer.vue'

  export default {
    name: 'BeerCard',
    components: {
      ButtonRandomBeer
    },

    data () {
      return {
        brand: '',
        name: '',
        style: '',
        alcohol: '',
        blg: ''
      }
    },

    async mounted () {
      await this.randomBeer();
      this.loading = false;
    },

    methods: {
      async randomBeer() {
        try {
          const response = await axios.get("https://random-data-api.com/api/beer/random_beer");
          this.brand = response.data.brand;
          this.name = response.data.name;
          this.style = response.data.style;
          this.alcohol = response.data.alcohol;
          this.blg = response.data.blg;
        } catch(e) {
          console.log(e);
          this.errored = true;
        }
      }
    }  
  }
</script>

<style module lang="scss">
@import '~@/styles/mixin.scss';

.beer {
  width: 550px;
  padding: 30px;
  border-radius: 10px;
  background-color: var(--common);
  box-shadow: 0px 5px 10px 2px rgba(34, 60, 80, 0.2);

  @include screen-l {
    width: 100%;
  }

  p {
    font-size: 35px;
    line-height: 120%;
    letter-spacing: 0.03em;
  }

  ul {
    max-width: max-content;
    text-align: left;
    list-style: none;
    padding: 0;
    margin: 0;
  }

  li {
    margin-bottom: 10px;
    font-weight: 400;
    font-size: 24px;
    line-height: 110%;
    letter-spacing: 0.06em;
  }
}
</style>