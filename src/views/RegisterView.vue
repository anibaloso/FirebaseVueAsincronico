<script setup>
import { ref } from 'vue'
import { $auth } from '@/firebaseApp'
import { createUserWithEmailAndPassword } from 'firebase/auth'
import RegistroGoogle from '@/components/RegistroGoogle.vue'

const email = ref('')
const password = ref('')

async function handleRegister() {
    try {
        await createUserWithEmailAndPassword($auth, email.value, password.value)
        email.value = ''
        password.value = ''
        alert('Felicidades Usuario Creado ✨')
    } catch (error) {
        console.error('falla al guardar el usuario')
        alert('Lo sentimos falla al crear el usuario')
    }
}

</script>
<template>

    <form class="registro" @submit.prevent="handleRegister">
        <label for="email">Ingrese Email</label>
        <input type="email" v-model="email" required>
        <label for="password">Ingrese password</label>
        <input type="password" v-model="password" required>
        <button type="submit">Registrar</button>


    </form>

    <RegistroGoogle />

</template>