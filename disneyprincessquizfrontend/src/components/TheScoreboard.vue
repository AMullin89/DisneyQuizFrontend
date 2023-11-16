<template>
    <div id="container">
        <header>
            <h3>Score</h3>
        </header>
        <section>
            <p>Score:</p>
            <p>{{ score }}</p>
            <p>Lives:</p>
            <p>{{ lives }}</p>
            <p>Princes Banished:</p>
            <p> {{ princes }}</p>

        </section>
    </div>
</template>

<script>
export default {
    props: ['score', 'princes', 'lives'],
    
}
</script>

<style scoped>
#container {
    width: 20%;
    border: 1px solid black;
    border-radius: 15px;
    box-shadow: 2px 2px 5px black;
    margin: 3rem 3rem 0 3rem;

}



header {
    background-color: #ffcbe1;
    padding-top: 0;
    border-radius: 15px 15px 0 0;
}

section {
    text-align: center;
    margin-bottom: 1rem;
    display: flex;
    flex-direction: column;
    
}

h3 {
    text-align: center;
    margin: 0 0;
    padding: 1rem 1rem;
    font-size: 3rem;
}


p {
    text-align: center;
    font-size: 1.5rem;
    margin-top: 0.4rem;
    margin-bottom: 0.2rem;
}

menu {
    text-align: center;
    margin: 0 0;
    padding: 0 0;
}

button {
    border: none;
    font-family: inherit;
    font-weight: 800;
    font-size: 2rem;
    background-color: #f2e0e9;
    margin-bottom: 1rem;

}

button:hover {
    cursor: pointer;
    transform: scale(1.2);
}
</style>