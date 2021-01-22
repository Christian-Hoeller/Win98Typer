<template>
    <div>
        <div class="box">
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
    color: gray;
}

.wrong{
    color:red;
}

.default{
    color:text;
}

.current{
    color:indigo;
}

.box{
 --gap: 12px;
  display: inline-flex;
  flex-wrap: wrap;
  margin: calc(-1 * var(--gap)) 0 0 calc(-1 * var(--gap));
  width: calc(100% + var(--gap));
}

.box > *{
    margin: var(--gap) 0 0 var(--gap);
}

</style>