<script setup>
const props = defineProps(['num1', 'num2', 'ope', 'atualizarVariaveis', 'mudarOperador']);
const emit = defineEmits(['update:num1', 'update:num2', 'update:ope']);

const handleNum1Change = (event) => {
    emit('update:num1', event.target.value);
    props.atualizarVariaveis(event.target.value, '1');
};

const handleNum2Change = (event) => {
    emit('update:num2', event.target.value);
    props.atualizarVariaveis(event.target.value, '2');
};

const handleOpeChange = (event) => {
    emit('update:ope', event.target.value);
    props.mudarOperador(event.target.value);
};
</script>

<template>
    <form class="numbers mt-5 ps-5 pe-5 d-flex justify-content-between">
        <input type="number" class="fs-1 py-3 rounded-4  ms-5 me-5 bg-light" :value="props.num1"
            @keyup="handleNum1Change" />
        <select :value="props.ope" @change="handleOpeChange" class="form-control">
            <option value=""></option>
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="/">/</option>
            <option value="*">*</option>
        </select>
        <input type="number" class="fs-1 py-3 rounded-4  ms-5 me-5 bg-light" :value="props.num2"
            @keyup="handleNum2Change" />
    </form>
</template>

<style scoped>

.numbers{

}
select {
    width: 60px;
    text-align: center;
    background-color: transparent;
    color: white;
    font-size: 20px;
}

select:hover {
    cursor: pointer;
    background-color: #ffaa50;
}

select:active {
    background-color: transparent;
}

select::selection {
    background-color: transparent;
}

input {
    text-align: center;
    border: none;
    width: 100px;
}

input[type="number"]::-webkit-outer-spin-button,
input[type="number"]::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
}

input[type="number"] {
    -moz-appearance: textfield;
}
</style>
