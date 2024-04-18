<template>
<div class="container">
    <img src="../static/nuvens.svg" alt="" srcset="" class="img-nuvem">

    <img src="../static/nuvens.svg" alt="" srcset="" class="img-nuvem-one">

    <img src="../static/nuvens.svg" alt="" srcset="" class="img-nuvem-buttom">

</div>
</template>
  
<script setup>
  
</script>
  
<style scoped lang="scss">
.container {
    width: 100%;
    height: 100vh;
    display: grid;
    // grid-template-rows: 1fr min-content min-content min-content min-content min-content min-content min-content min-content min-content min-content min-content min-content;
    grid-template-columns: repeat(12, 1fr);
}

.img-nuvem {
    grid-area: 2 / 1 / span 4 / span 2;
}

.img-nuvem-one {
    grid-row: 5 / span 7;
    grid-column: 5 / span 5;
}

.img-nuvem-buttom {
    grid-area: 9 / 12;
}

/* Estilos responsivos para telas menores */
@media (max-width: 768px) {
    
    .img-nuvem {
        grid-area: 2 / 1 / span 4 / span 2;
    }
    .img-nuvem-one {
        grid-row: 5 / span 7;
        grid-column: 5 / span 5;
    }
    .img-nuvem-buttom {
        grid-area: 9 / 12;
    }
}

/* Estilos para imagens responsivas */
// .img-nuvem,
// .img-nuvem-one,
// .img-nuvem-buttom {
//     width: 100%;
//     height: auto;
// }
</style>