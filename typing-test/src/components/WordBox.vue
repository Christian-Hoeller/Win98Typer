<template>
    <div>
        <div>
            <span v-for="(word, index) in words" :key="index" :class="word.state">{{word.word}}</span>
        </div>
    </div>
</template>

<script>

export default {
    name:"WordBox",
    props:{
        words: Array
    },
    data(){
        return{
            isCorrect:false,
            isWrong:true,
        }
    }
}
</script>

<style>

.correct{
    color: green;
}

.wrong{
    color:red;
}

.default{
    color:blueviolet;
}


</style>