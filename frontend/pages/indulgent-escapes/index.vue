<template>
  <div class="container">
    <div v-for="hotel in hotels" :key="hotel.id">
      <Hotel
        :hotel="hotel"
        :hotelBrand="hotel.brand.name"
        :hotelSlug="hotel.brand.slug"
        :hotelImage="hotel.image[0].url"
      />
    </div>
  </div>
</template>

<script>
import hotelQuery from "~/apollo/queries/hotel/hotels";

export default {
  data() {
    return {
      hotels: []
    };
  },
  apollo: {
    hotels: {
      prefetch: true,
      query: hotelQuery
    }
  },
  layout: "indulgent"
};
</script>

<style></style>
