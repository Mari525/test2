<template>
  <div class="modal">
    <form class="modal__form">
      <input v-model="newCard.title" placeholder="Название" required>
      <textarea v-model="newCard.description" placeholder="Описание" rows="4"></textarea>
      <input v-model="newCard.price" placeholder="Цена" required>
      <input v-model="newCard.members" placeholder="Участники">
      <input v-model="newCard.receipts" placeholder="Чеки">
      <input v-model="newCard.period" placeholder="Период">
      <input v-model="newCard.design" placeholder="Конструктор">

      <div class="modal__btn-wrapper">
        <button @click="save">Сохранить</button>
        <button @click="$emit('close')">Закрыть</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';

const emit = defineEmits();
const newCard = ref({
  title: '',
  description: '',
  price: '',
  members: '',
  receipts: '',
  period: '',
  design: '',
});

function save() {
  if (newCard.value.title && newCard.value.description && newCard.value.price) {
    emit('save', { ...newCard.value });
    resetForm();
  }
}

function resetForm() {
  newCard.value = {
    title: '',
    description: '',
    price: '',
    members: '',
    receipts: '',
    period: '',
    design: '',
  };
}
</script>


<style lang="scss">
  .modal {

    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;  

    &__form {
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
      max-width: 500px;
      width: 100%;
      padding: 20px;

      border-radius: 10px;
      background-color: #ffffff;
      border: 1px solid $color-accent;

      display: flex;
      flex-direction: column;
      gap: 20px;
    }

    input,
    textarea,
    button {
      padding: 10px;

      font-size: 1.6rem;
      font-family: $font-primary;
      border-radius: 5px;
      border: 1px solid $color-accent;
    }

    textarea {
      resize: none;
    }

    &__btn-wrapper {
      display: flex;
      justify-content: space-between;
      gap: 40px;
    }

    button {
      height: 40px;
      width: 200px;

      background-color: $color-accent;
      color: #ffffff;
      border: none;
    }
    
  }

</style>

