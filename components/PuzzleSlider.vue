<template>
    <div class="container">
      <div class="puzzle-board">
        <div
          v-for="(number) in numbers"
          :key="number"
          :id="'tile-' + number"
          :class="{ 'tile': number !== 9, 'empty-tile': number === 9 }"
          @click="moveTile(number)"
        >
          {{ number !== 9 ? number : '' }}
        </div>
      </div>
      <div style="display: flex; gap: 10px;">
        <button @click="checkPuzzle" class="btn-finalizar">Finalizar</button>
        <button @click="checkPuzzle" class="btn-finalizar">Finalizar</button>
      </div>
    </div>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue';
  
  export default {
    name: 'PuzzleSlider',
    setup() {
      const numbers = ref([]);
      const winningOrder = [1, 2, 3, 4, 5, 6, 7, 8 ];
  
      const initializeGame = () => {
        numbers.value = shuffleArray([...winningOrder]);
        // Ensure the empty space is always at the end
        numbers.value.push(9);
      };
  
      const shuffleArray = (array) => {
        let currentIndex = array.length, randomIndex;
        while (currentIndex !== 0) {
          randomIndex = Math.floor(Math.random() * currentIndex);
          currentIndex--;
          [array[currentIndex], array[randomIndex]] = [array[randomIndex], array[currentIndex]];
        }
        return array;
      };
  
      const moveTile = (clickedNumber) => {
        const clickedIndex = numbers.value.indexOf(clickedNumber);
        const emptyIndex = numbers.value.indexOf(9);
  
        if (canMove(clickedIndex, emptyIndex)) {
          // Swap the clicked tile with the empty space
          numbers.value.splice(emptyIndex, 1, clickedNumber);
          numbers.value.splice(clickedIndex, 1, 9);
        }
      };
  
      const canMove = (clickedIndex, emptyIndex) => {
        // Check if the clicked tile is adjacent to the empty space
        const clickedRow = Math.floor(clickedIndex / 3);
        const clickedCol = clickedIndex % 3;
        const emptyRow = Math.floor(emptyIndex / 3);
        const emptyCol = emptyIndex % 3;
  
        return (
          (Math.abs(clickedRow - emptyRow) === 1 && clickedCol === emptyCol) ||
          (Math.abs(clickedCol - emptyCol) === 1 && clickedRow === emptyRow)
        );
      };
  
      const checkPuzzle = () => {
        if (JSON.stringify(numbers.value.slice(0, 8)) === JSON.stringify(winningOrder)) {
            console.log(JSON.stringify(numbers.value.slice(0, 8)))
          alert('Parabéns! Você resolveu o quebra-cabeça!');
        } else {
            console.log(JSON.stringify(numbers.value.slice(0, 8)))
          alert('Ainda não está resolvido. Continue tentando!');
        }
      };
  
      onMounted(() => {
        initializeGame();
      });
  
      return {
        numbers,
        moveTile,
        checkPuzzle
      };
    }
  };
  </script>
  
  <style scoped>
  .container{
    display: grid;
    place-items: center;
    gap: 10px;
    position: relative;
  }
  .puzzle-board {
    display: grid;
    grid-template-columns: repeat(3, 80px);
    gap: 10px;
    background-color: white;
    box-shadow: 4px 2px 2px 2px rgba(180, 158, 158, 0.2);
    width: 100%;
    max-width: 310px;
    padding: 10px;
    border-radius: 18px;
  }
  .btn-finalizar{
    width: 120px;
    height: 3rem;
    background-color: #9133B7;
    color: white;
    border: none;
    border-radius: 4px;
  }
  
  .tile {
    width: 80px;
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    border: 1px solid white;
    cursor: pointer;
    display: flex;
            
    background-color: #4CAF50;
    color: white;
    font-size: 20px;
    cursor: pointer;
    transition: background-color 0.3s;
/* 
    &:hover {
        background-color: darken(#4CAF50, 10%);
    } */
  }
  
  .empty-tile {
    visibility: hidden;
    
  }

  </style>
  