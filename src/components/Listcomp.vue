<script setup>

const props = defineProps(['lis']);

</script>

<template>
    <div class="list-items">
        <p>log:</p>
        <ul>
            <li v-for="lista in props.lis">{{ lista }}</li>
        </ul>
    </div>
</template>

<style scoped>
.list {
    background-color: #272a31;

}

.list-items {
    text-align: start;
}

ul {
    list-style: none;
    text-align: start;
    background-color: #2e3036;
    max-height: 500px;
    overflow-y: auto;
    scrollbar-color: transparent;
    border: none;
    border-top: 1px solid white;
}
</style>