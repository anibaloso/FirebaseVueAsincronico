<script setup>

import { ref } from 'vue'
import { $auth } from '@/firebaseApp'
import { signInWithEmailAndPassword } from 'firebase/auth'

const email = ref('')
const password = ref('')

async function handleLogin(){
    try {
        await signInWithEmailAndPassword($auth,email.value,password.value)
        alert('Felicidades estas Logueado ✨')
    } catch (error) {
        console.error('falla al loguear')
        alert('Hubo un problema al ingresar 😿')
    }
}

</script>

<template>
    <h2>Inicia Sesión</h2>
    <form @submit.prevent="handleLogin">
        <label for="email">Ingresa Correo</label>
        <input type="email" id="email" v-model="email" required>
        <label for="password">Ingresa password</label>
        <input type="text" id="password" v-model="password" required>
        <button type="submit">Login</button>
    </form>
</template>