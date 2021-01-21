<template>
<div>
    <WordBox v-bind:words="words" />
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
            words: this.getWords()
        }
    },
    methods: {
        getWords(){
            return json[0].words;
        }
    }
}
</script>