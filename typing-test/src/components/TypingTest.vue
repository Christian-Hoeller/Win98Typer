<template>

<div class="flex justify-center items-center w-screen h-screen">

<div class="window w-1/2" >
  <div class="title-bar">
    <div class="title-bar-text">A Window With Stuff In It</div>
    <div class="title-bar-controls">
      <button aria-label="Minimize"></button>
      <button aria-label="Maximize"></button>
      <button aria-label="Close"></button>
    </div>
  </div>
  <div class="window-body">
    <WordBox v-bind:words="words" />
    <div class="flex">
     <input type="text" @input="handleKeyPress" v-model="userInput" class="input">
    <button @click="reset" class="reset">Restart</button>
    </div>
    <p>word index: {{wordIndex}}</p>
  </div>
</div>



</div>
</template>

<script>
import WordBox from './WordBox';
import json from '../utils/words.json'

export default {
    name:"TypingTest",
    components:{
        WordBox,
    },
    data(){
        return{
            userInput: '',
            currentWordIndex: 0,
            words: this.getWordsWithClasses(),
        }
    },
    methods: {
        getWordsWithClasses(){
            const wordSet = json[0].words;
            let words = [];
            const wordAmount = 25
            // const wordAmount = 50;
            for(let i = 0; i <= wordAmount; i++){
                const randomIndex = Math.floor(Math.random() * wordSet.length);
                words.push(wordSet[randomIndex]);
            }
            words = words.map(word => ({state:'default', word: word}));
            words[0].state = 'current';
            return words;
        },
        getWordByIndex(index){
            return this.words[index].word;
        },
        handleKeyPress(){
            let currentWord = this.getWordByIndex(this.currentWordIndex);
            
            if(this.userInput[this.userInput.length - 1] === ' '){
                
                // Check if word is true
                if(currentWord === this.userInput.split(' ')[0]){
                    this.words[this.currentWordIndex].state = "correct";
                }
                else{
                    this.words[this.currentWordIndex].state = "wrong"
                }

                // reset user input
                this.userInput = '';

                // check if last word
                if(this.currentWordIndex !== this.words.length - 1){
                    this.currentWordIndex ++;
                    this.words[this.currentWordIndex].state = "current"
                    
                }
            }
            else{
                if(currentWord.startsWith(this.userInput)){
                    this.words[this.currentWordIndex].state = "current"

                }
                else{
                    this.words[this.currentWordIndex].state = "wrong"

                }
            }
        },
        reset(){
            this.words = this.getWordsWithClasses();
            this.currentWordIndex = 0;
            this.userInput = '';

        }
    },
    computed:{
        wordIndex() {
            return this.currentWordIndex;
        }
    }
}
</script>

<style >

    /* .input{
        width: 70%;
        font-size: large;
    }

    .reset{
        margin-left: 10px;
        width: 20%;
    } */

  
</style>