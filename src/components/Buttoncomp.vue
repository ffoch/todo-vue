<script setup>

const props = defineProps(['limpa','adiciona']);
</script>


<template>
    <form @submit.prevent class="operators p-5 mb-4 mt-4 d-flex justify-content-center">
            <button type="button" class="fs-1 ms-2 me-3 p-3 rounded-5" @click="props.limpa">C</button>
            <button type="button" class="fs-1 ms-2 me-3 p-3 rounded-5" @click="props.adiciona">></button>
    </form>
</template>


<style scoped>


button{
    background-color: #FE941F;
    color: #292929;
    cursor: pointer;
    border: none;
}

button:hover{
    background-color: #ffaa50;
}
</style>