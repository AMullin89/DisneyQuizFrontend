<template>
    <div>
        <dialog open>
            <header>
                <h2>Please Enter Your Name</h2>
            </header>
            <section>
                <label for="name">And what was that young princesses' name?</label>
                <input type="text" name="name" id="name" @change="getPlayerName">
            </section>
            <menu>
                <button @click="sendPlayerName">Continue</button>
            </menu>
        </dialog>
    </div>
</template>

<script>
export default {
    data(){
        return {
            playerName: '',
            questions: []
        }
    },
    methods: {
        getPlayerName(event){
            this.playerName = event.target.value;
        },
        async getQuestions(){
            
           await fetch('http://localhost:3000/questions').then(response =>{
                if (response.ok){
                    return response.json();
                }
            }).then((data) =>{
                this.questions = data;
            })
        },
        sendPlayerName() {
            this.$emit('player-name', this.playerName);
            console.log(this.questions);
            this.$emit('questions', this.questions);
        }
    },
    beforeMount(){
        this.getQuestions();
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

section {
    text-align: center;
}

label {
    text-align: center;
    font-size: 1.5rem;
    display: block;
}


input {
    width: 60%;
    margin: 1rem 0;
    height: 2rem;
    font-family: inherit;
    font-size: 2rem;
    text-align: center;
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