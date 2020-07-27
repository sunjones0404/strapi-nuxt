<template>
  <div :class="hotelSlug">
    <div class="hotel">
      <div class="hotel__brand">
        {{ hotelBrand }}
      </div>
      <div class="hotel__image-wrapper">
        <img class="hotel__image" :src="'http://localhost:1337' + hotelImage" />
      </div>
      <div class="hotel__info">
        <p class="hotel__title">{{ hotel.name }}</p>
        <p class="hotel__info-text">
          <fa class="hotel__info-icon" :icon="['fas', 'map-marker-alt']" />{{
            hotel.location
          }}
        </p>
        <br />
        <p class="hotel__info-text">
          <fa class="hotel__info-icon" :icon="['fas', 'utensils']" />{{
            hotel.catering
          }}
        </p>
        <p class="hotel__info-text">
          <fa class="hotel__info-icon" :icon="['fas', 'key']" />{{
            hotel.rooms
          }}
        </p>
        <p class="hotel__info-text">
          <fa class="hotel__info-icon" :icon="['fas', 'suitcase']" />{{
            hotel.baggage
          }}
        </p>
        <p class="hotel__info-text">
          <fa class="hotel__info-icon" :icon="['fas', 'life-ring']" />{{
            hotel.protection
          }}
        </p>
        <p class="hotel__info-text">
          <fa class="hotel__info-icon" :icon="['fas', 'bus']" />{{
            hotel.transport
          }}
        </p>
      </div>
      <div class="hotel-pricing">
        <div class="hotel-pricing__rating">
          <p class="hotel-pricing__rating-text">Our rating</p>
          <div>
            <fa
              class="hotel-pricing__rating-icon"
              :icon="['fas', 'star']"
              v-for="i in hotel.rating"
              :key="i"
            />
          </div>
        </div>
        <div class="hotel-pricing__info">
          <p class="hotel-pricing__text">Price per person</p>
          <p class="hotel-pricing__price">£{{ hotel.price }}</p>
        </div>
        <button class="hotel__btn">{{ hotel.button_text }}</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    hotel: {
      type: Object,
      default: () => ({
        value: ""
      })
    },
    hotelBrand: {
      type: String,
      default: ""
    },
    hotelSlug: {
      type: String,
      default: ""
    },
    hotelImage: {
      type: String,
      default: ""
    }
  }
};
</script>

<style lang="scss">
.hotel {
  position: relative;
  height: 200px;
  background: var(--card-bg);
  display: flex;
  flex-direction: row;
  margin: 25px 0 0;
  border: 1px solid var(--primary);
  border-radius: 5px;
  overflow: hidden;

  &:last-child {
    margin-bottom: 30px;
  }

  &__brand {
    position: absolute;
    top: 5px;
    left: 5px;
    background: var(--primary);
    padding: 5px;
    font-size: 12px;
    color: var(--white);
    border-radius: 2px;
  }

  &__image {
    width: 100%;
    height: 100%;
    object-fit: cover;

    &-wrapper {
      height: 100%;
      width: 30%;
    }
  }

  &__title {
    font-size: 24px;
    color: var(--primary-dark);
  }

  &__info {
    width: 40%;
    padding: 20px;
    background: var(--white);

    &-text {
      font-size: 14px;
      line-height: 1.3;
      color: var(--dark-text);
    }

    &-icon {
      font-size: 11px;
      margin-right: 5px;
      color: var(--primary);
    }
  }

  &-pricing {
    width: 30%;
    padding: 20px;
    display: flex;
    align-items: flex-end;
    flex-direction: column;
    justify-content: space-between;

    &__text {
      color: var(--primary);
    }

    &__rating {
      height: 100%;
      width: 100%;
      display: flex;
      flex-direction: row;
      justify-content: space-between;

      &-text {
        color: var(--primary);
      }

      &-icon {
        color: var(--primary);
      }
    }

    &__info {
      width: 100%;
      display: flex;
      justify-content: space-between;
      align-items: flex-end;
      margin-bottom: 20px;
    }

    &__price {
      font-size: 30px;
      font-weight: 700;
      color: var(--primary);
    }
  }

  &__btn {
    display: block;
    width: 100%;
    background-color: var(--card-btn);
    padding: 10px 12px;
    font-size: 18px;
    line-height: 18px;
    text-align: center;
    color: var(--white);
    border: 0;
    border-radius: 4px;
    border-bottom: 3px solid var(--card-btn-dark);
    transition: background-color 0.2s linear;
    cursor: pointer;
  }
}
</style>
