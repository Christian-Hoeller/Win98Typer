<template>

<div>
    <WordBox v-bind:words="words" />
    <div>
        <input type="text" @input="handleKeyPress" v-model="userInput">
        <p>word index: {{wordIndex}}</p>
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
            
            if(this.userInput[this.userInput.length - 1] === ' '){
                
                let currentWord = this.getWordByIndex(this.currentWordIndex);
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
        }
    },
    computed:{
        wordIndex() {
            return this.currentWordIndex;
        }
    }
}
</script>