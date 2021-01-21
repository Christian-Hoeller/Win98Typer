<template>
    <div>
        <div>
            <span v-for="(word, index) in words" :key="index">{{word}}</span>
        </div>
    </div>
</template>

<script>

export default {
    name:"WordBox",
    props:{
        words: Array
    }
}
</script>