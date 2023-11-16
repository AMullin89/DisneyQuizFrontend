<template>
    <div id="grid">
        <div class="square" :class="{active: score < 6}"><img src="../assets/belle.png"></div>
        <div class="square" :class="{ active: score > 5 && score < 11 }"><img src="../assets/aerial.png"></div>
        <div class="square" :class="{ active: score > 10 && score < 16 }"><img src="../assets/aurora.png"></div>
        <div class="square" :class="{ active: score > 15 && score < 21 }"> <img src="../assets/elsa.png"></div>
        <div class="square" :class="{ active: score > 20 && score < 26 }"><img src="../assets/cinderella.png"></div>
        <div class="square" :class="{ active: score > 25 && score < 31 }"><img src="../assets/jasmine.png"></div>
        <div class="square" :class="{ active: score > 30 && score < 36 }"><img src="../assets/rapunzel.png"></div>
        <div class="square" :class="{ active: score > 35 && score < 41 }"><img src="../assets/snowwhite.png"></div>
        <div class="square" :class="{ active: score > 40 && score < 46 }"><img src="../assets/tiana.png"></div>
        <div class="square" :class="{ active: score > 45 && score < 51 }"><img src="../assets/vecteezy_watercolour-pastel-fairytale-clipart-ai-generative_24172390_636.png"></div>
    </div>
</template>

<script>
export default {
    props: ['score'],
    data(){
        return {
        }
    }
}

</script>

<style scoped>

#grid {
    display: grid;
    grid-template-columns:  8rem 8rem 8rem 8rem 8rem;
    grid-template-rows: 8rem 8rem 8rem 8rem;
    gap: 10px;
    width: 80%;
    margin: 2rem auto;
    justify-content: center;
}

.square {
    background-color: #e2c8f6;
    border-radius: 10px;
    box-shadow: 2px 2px 2px black;
}

img {
    height: 100%;
    width: 100%;
    object-fit: contain;
}

.active {
    border: 5px solid black;
}

</style>

