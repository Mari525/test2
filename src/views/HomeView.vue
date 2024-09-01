<script setup>
  import Card from '../components/Card.vue'
  import Modal from '../components/Modal.vue'
</script>

<template>
  <main class="main">
    <h1 class="main__heading">Тарифы</h1>
    <ul class="main__list">
      <Card />
    </ul>
    <Modal />
  </main>
</template>

<style lang="scss">
  .main {
    &__heading {
      margin-bottom: 58px;
      font-size: 5.7rem;
      font-weight: 600;
      line-height: 6.3rem;
      font-family: $font-demi;
    }

    &__list {
      display: flex;
      justify-content: space-between;
      flex-wrap: wrap;
    }
  }
</style>