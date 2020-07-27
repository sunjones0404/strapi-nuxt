<template>
  <div class="outer">
    <div class="hub">
      <nav class="hub-container container">
        <ul class="hub-nav-menu hub-wrapper">
          <li
            class="hub-nav-menu__item"
            v-for="brand in brands"
            :key="brand.id"
          >
            <router-link
              :to="'/' + (brand.slug === 'jet2holidays' ? '' : brand.slug)"
              tag="a"
              class="hub-nav-menu__link"
              >{{ brand.name }}
            </router-link>
          </li>
        </ul>
      </nav>
    </div>
    <div class="container">
      <img
        class="logo"
        :src="'http://localhost:1337' + brands[brandType].logo[0].url"
      />
    </div>
    <div class="navbar">
      <div class="container">
        <ul class="navbar__list">
          <li class="navbar__list-item">
            Holiday types
            <fa class="navbar__list-icon" :icon="['fas', 'chevron-down']" />
          </li>
          <li class="navbar__list-item">
            Destinations
            <fa class="navbar__list-icon" :icon="['fas', 'chevron-down']" />
          </li>
          <li class="navbar__list-item">
            Deals
            <fa class="navbar__list-icon" :icon="['fas', 'chevron-down']" />
          </li>
          <li class="navbar__list-item">
            More
            <fa class="navbar__list-icon" :icon="['fas', 'chevron-down']" />
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import brandsQuery from "~/apollo/queries/brand/brands";

export default {
  props: ["brandType"],
  data() {
    return {
      brands: []
    };
  },
  apollo: {
    brands: {
      prefetch: true,
      query: brandsQuery
    }
  }
};
</script>
