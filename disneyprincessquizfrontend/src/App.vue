<template>
  <welcome-dialog v-if="gameStart" @start-game="startGame"></welcome-dialog>
  <name-dialog v-if="!gameStart && !playerName" @player-name="setPlayerName" @questions="setQuestions"></name-dialog>
  <start-dialog :playerName="playerName" v-if="playerName && !startQuestions" @start-questions="beginQuestions"></start-dialog>
  <beast-dialog v-if="showBeast"  @close-beast="closeBeast"></beast-dialog>
  <eric-dialog v-if="showEric" @close-eric="closeEric"></eric-dialog>
  <phillip-dialog v-if="showPhillip" @close-phillip="closePhillip"></phillip-dialog>
  <hans-dialog v-if="showHans" @close-hans="closeHans"></hans-dialog>
  <game-over v-if="gameOver" :playerName="playerName" :princes="princes" :questions="questionNumber" @reset="resetGame"></game-over>
  <main-header></main-header>
  <div id="gamescreen">
    <question-dialog v-if="startQuestions" :number="questionNumber" :question="currentQuestion" @correct-answer="setNextQuestion" @wrong-answer="wrongAnswer"></question-dialog>
    <the-scoreboard :score="score" :lives="lives" :princes="princes" v-if="startQuestions"></the-scoreboard>
  </div>
  <progress-board :score="score" v-if="startQuestions"></progress-board>
</template>

<script>
import MainHeader from './components/MainHeader.vue'
import WelcomeDialog from './components/WelcomeDialog.vue'
import NameDialog from './components/NameDialog.vue'
import StartDialog from './components/StartDialog.vue'
import QuestionDialog from './components/QuestionDialog.vue'
import TheScoreboard from './components/TheScoreboard.vue'
import ProgressBoard from './components/ProgressBoard.vue'
import BeastDialog from './components/BeastDialogue.vue'
import GameOver from './components/GameOver.vue'
import EricDialog from './components/EricDialog.vue'
import PhillipDialog from './components/PhillipDialog.vue'
import HansDialog from './components/HansDialog.vue'




export default {
  components: { 
    MainHeader,
    WelcomeDialog,
    NameDialog,
    StartDialog,
    QuestionDialog,
    TheScoreboard,
    ProgressBoard,
    BeastDialog,
    GameOver,
    EricDialog,
    PhillipDialog,
    HansDialog

   },
  data() {
    return {
      gameStart: true,
      playerName: '',
      startQuestions: false,
      currentQuestion: {
        question: '',
        ans1: '',
        ans2: '',
        ans3: '',
        ans4: '',
        correctAns: ''
      },
      questions: [],
      score: 0,
      lives: 3,
      questionNumber: 1,
      princes: 0,
      gameOver: false,
      showBeast: false,
      showEric: false,
      showPhillip: false,
      showHans: false
    }
  },
  methods: {
    startGame(){
      this.gameStart = false;
    },
    setPlayerName(name){
      
      this.playerName = name;
      console.log(this.playerName);
    },
    beginQuestions(){
      this.startQuestions = true;
      console.log(this.questions);
    },
    setQuestions(questions){
      console.log(questions)
      this.questions = questions;

      const randomIndex = Math.floor(Math.random() * this.questions.length);
      this.currentQuestion = this.questions[randomIndex];

      let index = this.questions.findIndex(question => question.question === this.currentQuestion.question);
      this.questions.splice(index, 1);
      console.log(this.questions);
    },
    setNextQuestion(){

      if (this.questions.length === 0){
        console.log("No more questions")
      } else{ 
        const randomIndex = Math.floor(Math.random() * this.questions.length);
        this.currentQuestion = this.questions[randomIndex];

        let index = this.questions.findIndex(question => question.question === this.currentQuestion.question);
        this.questions.splice(index, 1);
      }
      this.score++;

      if (this.score === 5){
        this.princes++;
        this.showBeast = true;
      } else if (this.score === 10){
        this.princes++;
        this.showEric = true;
      } else if (this.score === 15){
        this.princes++;
        this.showPhillip = true;
      } else if (this.score === 20){
        this.princes++;
        this.showHans = true;
      }

      this.questionNumber++;


      

    },
    closeBeast(){
      this.showBeast = false;
    },
    closeEric(){
      this.showEric = false;
    },
    closePhillip(){
      this.showPhillip = false;
    },
    closeHans(){
      this.showHans = false;
    },
    wrongAnswer(){
      this.lives--;
      if (this.lives === 0){
        this.gameOver = true;
      }
    },
    resetGame(){
      this.playerName = '';
      this.gameStart = true;
      this.startQuestions = false;
      this.lives = 3;
      this.score = 0;
      this.questionNumber = 1;
      this.gameOver = false;
    }

  }



}

</script>



<style>

@import url('https://fonts.cdnfonts.com/css/new-walt-disney-font');

                

body {
  background-color: #f2e0e9;
  width: 100%;
  margin: 0 0;
  font-family: 'New Walt Disney Font', sans-serif;
}

#gamescreen {
  display: flex;
}



</style>
