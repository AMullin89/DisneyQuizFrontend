<template>
    <div id="container">
            <header>
                <h3>Question {{ number }}</h3>
            </header>
            <section>
                <h4 id="question">{{ question.question }}</h4>
                <div>
                    <input type="radio" id="ans1" name="ans" :value="question.ans1" v-model="selected" @click="getInput">
                    <label for="ans1">{{ question.ans1 }}</label>
                </div>
                <div>
                    <input type="radio" id="ans2" name="ans" :value="question.ans2" v-model="selected" @click="getInput">
                    <label for="ans2">{{ question.ans2 }}</label>
                </div>
                <div>
                    <input type="radio"  id="ans3" name="ans" :value="question.ans3" v-model="selected" @click="getInput">
                    <label for="ans3">{{ question.ans3 }}</label>
                    </div>
                <div>
                    <input type="radio" id="ans4" name="ans" :value="question.ans4" v-model="selected" @click="getInput">
                    <label for="ans4">{{ question.ans4 }}</label>
                </div>
                
            </section>
            <menu>
                <button @click="checkAnswer">Submit</button>
            </menu>
            <p v-if="wrongAnswer">Uh-oh, that wasn't the right answer, have a think and try again!</p>
    </div>
</template>

<script>
export default {
    props: ['question', 'number'],
    data() {
        return {
            answer: '',
            d_selected: '',
            wrongAnswer: false
        }
    },
    computed: {
        selected: {
            get(){
                return this.d_selected;
            },
            set(value){
                if (value === this.d_selected){
                    this.d_selected = false;
                } else {
                    this.d_selected = value;
                }
            }
        }
    },
    methods: {
        getInput(event){
            this.answer = event.target.value;
            console.log(this.answer);
        },
        checkAnswer(){
            if(this.answer === this.question.correctAns){
                console.log("Correct");
                this.$emit('correct-answer')
                this.d_selected = false;

                if( this.wrongAnswer === true){
                    this.wrongAnswer = false;
                }

            } else {
                console.log("Wrong!");
                this.wrongAnswer = true;
                this.$emit('wrong-answer');
            }
        }
    }
}
</script>

<style scoped>
#container {
    width: 70%;
    border: 1px solid black;
    border-radius: 15px;
    box-shadow: 2px 2px 5px black;
    margin: 3rem 0 0 3rem;
}



header {
    background-color: #ffcbe1;
    padding-top: 0;
    border-radius: 15px 15px 0 0;
}

section {
    text-align: center;
    margin-bottom: 1rem;
}

h3 {
    text-align: center;
    margin: 0 0;
    padding: 1rem 1rem;
    font-size: 3rem;
}

h4 {
    font-size: 2rem;
    margin: 1rem;
}

label {
    text-align: center;
    font-size: 1.5rem;
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
    background-color: #f2e0e9;
    margin-bottom: 1rem;
    
}

button:hover {
    cursor: pointer;
    transform: scale(1.2);
}


</style>