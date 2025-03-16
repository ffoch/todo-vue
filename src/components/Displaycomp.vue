<script setup>
const props = defineProps(['num1', 'num2', 'ope', 'res'])
</script>

<template>
<div class="dis pe-5 ps-5 w-50 py-4 rounded-3 text-light text-center col-md-5">
    <h5 v-if="props.num1 ==='' && props.num2 ==='' || props.ope ===''">math app</h5>
    <h5 v-else="props.num2 ===''">{{  props.num1 }} <span v-if="props.num1 !== '' && props.num2 !== ''">{{ props.ope }}</span>  {{ props.num2 }} <span v-if="props.num1 !== '' && props.num2 !== ''" >=</span></h5>
    
    <h1 v-if="props.ope ===''" style="color:#505050">__</h1>
    <h1 v-else="props.ope ===''">{{ props.res }}</h1>
</div>
</template>

<style scoped>
.dis{
    background-color:#505050 ;  
}

h5{
    text-align: end;
    font-weight: 100;
}

</style>