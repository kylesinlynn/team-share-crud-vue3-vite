<script setup>

import { ref } from 'vue'

const props = defineProps(['user'])
const emit = defineEmits(['create'])

const name = ref('') 
const age = ref(0)

function submitForm() {
    emit('create', name.value, age.value)
    name.value = ''
    age.value = 0
}

</script>

<template>

    <form @submit.prevent="submitForm">
        <label for="name">Name:</label>
        <input name="name" id="name" type="text" v-model="name" />
        <br/>
        <label for="age">Age:</label>
        <input name="age" id="age" type="number" v-model="age" />
        <br/>
        <button type="submit">➕</button>
    </form>

</template>

<style>

</style>