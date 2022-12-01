<script setup>

import { ref } from 'vue'

const props = defineProps(['user'])
const emit = defineEmits(['updateUser'])

const id = ref(props.user.id)
const name = ref(props.user.name)
const age = ref(props.user.age)

const update = ref(false)

function updateUser() {
    emit('updateUser', id, name, age)
    update.value = false
}

</script>

<template>

    <form @submit.prevent="updateUser" v-if="update">
        <input type="text" v-model="name" />
        <input type="number" v-model="age" />
        <button type="submit">✔️</button>
    </form>
    <span v-else>
        <p>{{ name }} || {{ age }}</p>
        <button type="button" @click="update = true">✒️</button>
    </span>

</template>

<style scoped>

</style>