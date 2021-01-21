<template>

<div>
    <WordBox v-bind:words="words" />
    <div>
        <input type="text" @input="handleKeyPress" v-model="userInput">
        <p>current word: {{currentWord}}</p> 
        <p>{{wordIndex}}</p>
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
            words: this.getWords(),
            userInput: '',
            currentWordIndex: 0,
            currentWord: this.getWords()[0],
        }
    },
    methods: {
        getWords(){
            return json[0].words;
        },
        getWordByIndex(index){
            return this.getWords()[index];
        },
        handleKeyPress(){
            
            if(this.userInput[this.userInput.length - 1] === ' '){
                
                let currentWord = this.getWordByIndex(this.currentWordIndex);
                // Check if word is true
                if(currentWord === this.userInput.split(' ')[0]){
                    console.log("word is correct");
                }
                else{
                    console.log("word is wrong")
                }

                // reset user input
                this.userInput = '';

                // inkrement currentWordIndex
                this.currentWordIndex ++;

                // inkrement currentword
                this.currentWord = this.getWordByIndex(this.currentWordIndex);
            }
        }
    },
    computed:{
        wordIndex() {
            return this.currentWordIndex;
        }
    }
}
</script>