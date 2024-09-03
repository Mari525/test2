<template>
  <main class="main">
    <h1 class="main__heading">Тарифы</h1>
    <ul class="main__list">
      <Card
        v-for="item in items"
        :key="item.id"
        :item="item"
        @openModal="openModal(item)"
      />
    </ul>
    <Modal
      v-if="isModalOpen"
      :item="selectedItem"
      @close="closeModal"
      @save="addCard"
    />
  </main>
</template>

<script setup>
import { ref } from 'vue';
import Card from '../components/Card.vue';
import Modal from '../components/Modal.vue';
import data from '../assets/data.json';

const items = ref(data);
const isModalOpen = ref(false);
const selectedItem = ref(null);

function openModal(item) {
  selectedItem.value = item;
  isModalOpen.value = true;
}

function closeModal() {
  isModalOpen.value = false;
  selectedItem.value = null;
}

function addCard(newCard) {
  items.value.push({ ...newCard, id: Date.now() });
  closeModal();
}
</script>



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
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      justify-items: stretch;
    }
  }
</style>