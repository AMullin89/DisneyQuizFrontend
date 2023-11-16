<template>
    <div>
        <dialog open>
            <header>
                <h2>Welcome</h2>
            </header>
            <section>
                <p>It is an honour to meet you Princess {{ playerName }}.</p>
                <p>You are about to embark on a challenging test of knowledge that will put these pesky Princes in their place once and for all.</p>
                <p>The whole kingdom wishes you luck!</p>
            </section>
            <menu>
                <button @click="startQuestions">Start</button>
            </menu>
        </dialog>
    </div>
</template>

<script>
export default {
    props: ['playerName'],
    data() {
        return {

        }
    },
    methods: {
        startQuestions() {
            this.$emit('start-questions');
        }
    }
}
</script>

<style scoped>
div {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 100%;
    background-color: rgba(0, 0, 0, 0.75);
    z-index: 10;
}

dialog {
    position: fixed;
    top: 20vh;
    left: 10%;
    border-radius: 15px;
    width: 80%;
    padding: 0;
}

header {
    background-color: #ffcbe1;
    padding-top: 0;
    border-radius: 15px 15px 0 0;
}

h2 {
    text-align: center;
    margin: 0 0;
    padding: 1rem 1rem;
    font-size: 4rem;
}

p {
    text-align: center;
    font-size: 1.5rem;
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
    background-color: white;
    margin-bottom: 1rem;
}

button:hover {
    cursor: pointer;
    transform: scale(1.2);
}
</style>