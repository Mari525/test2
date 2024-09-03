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
import { ref, onMounted } from 'vue';
import Card from '../components/Card.vue';
import Modal from '../components/Modal.vue';
import data from '../assets/data.json';

const items = ref([]);
const isModalOpen = ref(false);
const selectedItem = ref(null);

onMounted(() => {
  const savedItems = localStorage.getItem('items');
  if (savedItems) {
    items.value = JSON.parse(savedItems);
  } else {
    items.value = data;
  }
});

function openModal(item) {
  selectedItem.value = item;
  isModalOpen.value = true;
}

function closeModal() {
  isModalOpen.value = false;
  selectedItem.value = null;
}

function addCard(newCard) {
  const cardWithId = { ...newCard, id: Date.now() };
  items.value.push(cardWithId);
  localStorage.setItem('items', JSON.stringify(items.value));
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