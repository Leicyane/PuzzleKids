<template>
    <div class="card" @click="clickCard">
      <div class="card-inner" :class="{ flipped: card.flipped }">
        <div class="card-front">
          <img src="https://icones.pro/wp-content/uploads/2021/05/icone-question-violet.png" alt="" srcset="">
        </div>
        <div class="card-back">
          <img :src="card.imagem" :alt="card.name" />

        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Card',
    props: {
      card: Object,
    },
    methods: {
      clickCard() {
        this.$emit('card-clicked', this.card);
      },
    },
  };
  </script>
  
  <style scoped>
  .card {
    width: 100px;
    height: 140px;
    margin: 10px;
    perspective: 1000px;
    cursor: pointer;
  }
  .card-inner {
    width: 100%;
    height: 100%;
    position: relative;
    transform-style: preserve-3d;
    transition: transform 0.6s;
  }
  .card-inner.flipped {
    transform: rotateY(180deg);
  }
  .card-front, .card-back {
    position: absolute;
    width: 100%;
    height: 100%;
    backface-visibility: hidden;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 2em;
    object-fit: cover;
    flex-direction: column;  
  }
  img{
        width: 5.5rem;
    }
  .card-front {
    background: #333;
    color: white;
  }
  .card-back {
    background: white;
    transform: rotateY(180deg);
  }
  </style>
  