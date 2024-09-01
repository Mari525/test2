<template>
  <div class="modal">
    <form class="modal__form" action="#">
      <input v-model="newCard.title" type="text" placeholder="Название тарифа">
      <textarea v-model="newCard.description" rows="3" placeholder="Описание"></textarea>
      <input v-model="newCard.price" type="number" placeholder="Стоимость">
      <input v-model="newCard.members" type="text" placeholder="Участники">
      <input v-model="newCard.receipts" type="text" placeholder="Чеки">
      <input v-model="newCard.period" type="text" placeholder="Период">
      <input v-model="newCard.design" type="text" placeholder="Конструктор">
      <button @click="saveCard" type="button">Сохранить</button>
    </form>
  </div>
</template>

<style lang="scss">
  .modal {
    width: 265px;
    margin: 0 auto;

    border-radius: 10px;
    background-color: #ffffff;

    &__form {
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

    button {
      height: 40px;
      margin-bottom: 100px;

      background-color: $color-accent;
      color: #ffffff;
      border: none;
    }
    
  }


</style>

<script>
  export default {
    data() {
      return {
        showModal: false,
        newCard: {
          title: '',
          description: '',
          price: '',
          members: '',
          receipts: '',
          period: '',
          design: ''
        },
        cards: []
      };
    },
    mounted() {
      this.loadCards();
    },
    methods: {
      openModal() {
        this.showModal = true;
      },
      closeModal() {
        this.showModal = false;
        this.newCard = {
          title: '',
          description: '',
          price: '',
          members: '',
          receipts: '',
          period: '',
          design: ''
        }
      },
      saveCard() {
        this.cards.push({ ...this.newCard });
        this.saveCards();
        this.closeModal();
      },
      saveCards() {
        localStorage.setItem('cards', JSON.stringify(this.cards));
      },
      loadCards() {
        const savedCards = localStorage.getItem('cards');
        if (savedCards) {
          this.cards = JSON.parse(savedCards);
        }
      }
    }
  }
</script>