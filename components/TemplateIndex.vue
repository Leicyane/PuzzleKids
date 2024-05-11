<template>
    <div class="containerPage">
        <header> </header>
        <main>
            <h1 class="title">Quebra Cabeça</h1>
            <PuzzleSlider />
        </main>
    </div>
</template>


<style scoped lang="scss">
.containerPage {
    width: 100%;
    height: 100vh;
    position: absolute;
    z-index: 2;

    main {
        .title {
            color: #063B60;
        }

        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        height: 45vw;
        justify-content: center;

    }

    

}
</style>