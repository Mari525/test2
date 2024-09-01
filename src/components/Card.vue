<script>
  import data from '../assets/data.json'
  export default {
    data() {
      return {
        items: data
      }
  }
};
</script>

<template>
  <li class="card" v-for="item in items" :key="item.id">
    <div class="card__heading-wrapper">
      <span class="card__tariff">
        Тариф
      </span>
      <h2 class="card__heading">
        {{ item.title }}
      </h2>
    </div>
    <div class="card__descr-wrapper">
      <p class="card__text">
        {{ item.description }}
      </p>
      <span class="card__price"> {{ item.price }} </span>
      <p class="card__item" v-if="item.members"><span>{{ item.members }}</span> Участников</p>
      <p class="card__item" v-if="item.receipts"><span>{{ item.receipts }}</span> Чеков</p>
      <p class="card__item" v-if="item.period"><span>{{ item.period }}</span> Период</p>
      <p class="card__item" v-if="item.design"><span>{{ item.design }}</span> Конструктор</p>
      <button class="card__btn" @click="openModal">Запустить</button>
    </div>
  </li>
</template>

<style lang="scss">
  .card {
    max-width: 265px;
    color: $color-accent;
    margin-bottom: 40px;

    &__heading-wrapper {
      border-top-left-radius: 10px;
      border-top-right-radius: 10px;
      padding: 14px 0 19px;
      margin-bottom: 15px;
      background-color: $color-accent;
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    &__tariff {
      font-size: 1.6rem;
      line-height: 1.8rem;
      font-family: $font-primary;
      color: rgba(255, 255, 255, 53%);
    }

    &__heading {
      margin-top: 13px;
      color: #ffffff;
      font-family: $font-accent;
      letter-spacing: 0.05em;
      font-size: 2.4rem;
    }

    &__descr-wrapper {
      padding: 0 18px;
      border-left: 1px solid $color-accent;
      border-right: 1px solid $color-accent;

      display: flex;
      flex-direction: column;
      justify-content: space-between;
      height: 384px;
    }

    &__text {
      margin-bottom: 16px;

      font-size: 1.4rem;
      line-height: 1.8rem;
      font-family: $font-primary;
    }

    &__price {
      font-size: 3.2rem;
      line-height: 5.5rem;
      font-family: $font-heavy;
    }

    &__item {
      padding: 10px 0;
      display: flex;
      justify-content: space-between;
      align-items: center;

      border-bottom: 1px solid #D9D9D9;

      font-size: 1.4rem;
      font-family: $font-primary;

      span {
        font-family: $font-demi;
        font-weight: 600;
        font-size: inherit;
      }
    }

    &__btn {
      width: 141px;
      height: 41px;
      display: flex;
      justify-content: center;
      align-items: center;

      margin-top: auto;

      border: 1px solid $color-accent;
      border-radius: 8px;
      font-size: 1.6rem;
      background-color: #ffffff;
      

      &:hover {
        background-color: $color-accent;
        color: #ffffff;
      }

    }


  }
</style>