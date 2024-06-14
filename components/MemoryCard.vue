<template>
    <div class="containerGame">
      <header>
        <h1>JOGO DA MEMÓRIA</h1>
      </header>
      <VictoryModal v-if="showVictory" :errors="errors" @restart="restartGame" />
  
      <div class="corpo">
        
        <section class="jogo">
          <Card
            v-for="(card, index) in cards"
            :key="index"
            :card="card"
            @card-clicked="flipCard(card)"
          />
          <ButtonDefault @click.native="returnPage" title="Voltar" style="width: 30%;"/>
          <ButtonDefault @click.native="restartGame" title="Reiniciar" style="width: 30%;"/>
        </section>
        
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        cards: [],
        flippedCards: [],
        errors: 0,
        showVictory: false,
        winCounter: 0,
      };
    },
    mounted() {
      this.restartGame();
    },
    methods: {
      returnPage(){
          this.$router.push('/games')
      },
      shuffleCards(array) {
        return array.sort(() => Math.random() - 0.5);
      },
      generateCards() {
        const deck = [
          {
            id: 1,
            name: "Sapo",
            color: "#84CFFA",
            imagem: "https://thumbs.dreamstime.com/z/r%C3%A3-da-gordura-dos-desenhos-animados-76430879.jpg?w=768",
            descricao: ["descricao 1", "descricao 2", "descricao 3"],
            virado: true,
          },
          {
            id: 2,
            name: "Vaca",
            color: "#FA8484",
            imagem: "https://i.pinimg.com/originals/8d/aa/81/8daa8149edc1f6fe211017aa63e79e92.png",
            descricao: ["descricao 1", "descricao 2", "descricao 3"],
            virado: true,
          },
          {
            id: 3,
            name: "dog",
            color: "#E984FA",
            imagem: "https://png.pngtree.com/png-vector/20230120/ourmid/pngtree-veterinary-logo-design-dog-clipart-corgi-puppy-png-image_6565448.png",
            descricao: ["descricao 1", "descricao 2", "descricao 3"],
            virado: true,
          },
          {
            id: 4,
            name: "gato",
            color: "#84FAAC",
            imagem: "https://png.pngtree.com/png-clipart/20231110/original/pngtree-cartoon-cat-stickers-png-image_13525238.png",
            descricao: ["descricao 1", "descricao 2", "descricao 3"],
            virado: true,
          },
          {
            id: 5,
            name: "Jacare",
            color: "#8684FA",
            imagem: "https://thumbs.dreamstime.com/b/jacar%C3%A9-38125377.jpg",
            descricao: ["descricao 1", "descricao 2", "descricao 3"],
            virado: true,
          },
          {
            id: 6,
            name: "Elefante",
            color: "#F7FA84",
            imagem: "https://img.freepik.com/vetores-premium/elefante-sentado-e-sorrindo-em-um-branco-personagem_269543-14.jpg?w=740",
            descricao: ["descricao 1", "descricao 2", "descricao 3"],
            virado: true,
          },
        ];
  
        const duplicateDeck = deck.flatMap(card => [card, { ...card, id: card.id + deck.length }]);
        return this.shuffleCards(duplicateDeck.map(card => ({ ...card, flipped: false, matched: false })));
      },
      flipCard(card) {
        if (this.flippedCards.length < 2 && !card.flipped && !card.matched) {
          card.flipped = true;
          this.flippedCards.push(card);
          if (this.flippedCards.length === 2) {
            this.checkForMatch();
          }
        }
      },
      checkForMatch() {
        setTimeout(() => {
          const [card1, card2] = this.flippedCards;
          if (card1.name === card2.name) {
            card1.matched = true;
            card2.matched = true;
            this.winCounter++;
            if (this.winCounter === 6) {
              this.showVictory = true;
            }
          } else {
            card1.flipped = false;
            card2.flipped = false;
            this.errors++;
          }
          this.flippedCards = [];
        }, 1000);
      },
      restartGame() {
        this.cards = this.generateCards();
        this.flippedCards = [];
        this.errors = 0;
        this.showVictory = false;
        this.winCounter = 0;
      },
    },
  };
  </script>
  
  <style scoped>
  .containerGame {
    text-align: center;
    font-family: 'Ubuntu', sans-serif;
    text-align: center;
    color: white;

  }
  header {
    margin-bottom: 20px;
  }
  .corpo {
    display: flex;
    justify-content: center;

    
  }
  .jogo {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    width: 50%;
    margin: 0 20px;
  }
  #esq, #dir {
    width: 100px;
  }
  </style>
  