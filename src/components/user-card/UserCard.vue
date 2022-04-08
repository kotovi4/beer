<template>
  <section :class="$style.user">
    <div :class="$style.user__container">
      <img
        :src="avatar"
        alt="avatar"
        width="300"
        height="300"
      />
      <ul :class="$style.user__info">
        <li :class="$style.user__name"><b>{{ name }}</b>, {{ ageUser }}</li>
        <li :class="$style.user__post">{{ post }}</li>
      </ul>
    </div>
  </section>
</template>

<script>
import axios from 'axios';

export default {
  name: "UserCard",

  data () {
      return {
        avatar: '',
        name: '',
        age: '',
        post: '',
        errored: false,
        loading: true
      }
  },

  async mounted () {
    try {
      const response = await axios.get("https://random-data-api.com/api/users/random_user");
      this.avatar = response.data.avatar;
      this.name = response.data.first_name;
      this.age = response.data.date_of_birth;
      this.post = response.data.employment.title;
    } catch (e) {
      console.log(e);
      this.errored = true;
    } 
    
    this.loading = false;
  },

  computed: {
    ageUser() {
      return (new Date().getTime() - new Date(this.age)) / (24 * 3600 * 365.25 * 1000) | 0;
    }
  }
};
</script>

<style module lang="scss">
@import "~@/styles/mixin.scss";


.user {
  width: 350px;
  padding: 30px;
  margin-right: 80px;
  background-color: var(--common);
  border-radius: 10px;
  box-shadow: 0px 5px 10px 2px rgba(34, 60, 80, 0.2);

  @include screen-l {
    width: 100%;
    margin: 0 auto 35px;
  }
}

.user__container {
  display: flex;
  flex-direction: column;

  @include screen-l {
    flex-direction: row;
  }

  @include screen-s {
    flex-direction: column;
  }

  img {
    margin: 0 auto;
  }
}

.user__info {
  width: 100%;
  list-style: none;
  margin: 35px 0;
  padding: 0;
  text-align: left;
}

.user__name {
  margin: 10px 0;
  font-weight: 400;
  font-size: 35px;
  line-height: 120%;
  letter-spacing: 0.03em;

  @include screen-l {
    font-size: 48px;
  }

  @include screen-s {
    font-size: 35px;
  }
}

.user__post {
  font-weight: 400;
  font-size: 18px;
  line-height: 110%;
  letter-spacing: 0.06em;

  @include screen-l {
    font-size: 32px;
  }

  @include screen-s {
    font-size: 18px;
  }
}

img {
  position: relative;
}

img:before {
  position: absolute;
  content: "";
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-image: url("~@/assets/plug.jpeg");
}
</style>
