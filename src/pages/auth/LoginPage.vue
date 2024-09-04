<template>
    <div class="row justify-start items-start content-start login-container">
        <div class="col-5 login-form">
            <div class="header-login-form">
                <img src="/images/lamsel-logo.png" class="header-login-logo">
                <h1 class="header-login-form-label">Selamat datang!</h1>
                <p>Silahkan masukan email dan password untuk melanjutkan.</p>
            </div>
            <div class="form-input">
                <q-input v-model="email" type="email" outlined :dense="true" label="Email" :rules="[
                    val => !!val || 'Field wajib diisi'
                ]" />
                <q-input v-model="password" :type="isPwd ? 'password' : 'text'" outlined :dense="true"
                    label="Kata Sandi" :rules="[
                        val => !!val || 'Field wajib diisi'
                    ]">
                    <template v-slot:append>
                        <q-icon :name="isPwd ? 'visibility_off' : 'visibility'" class="cursor-pointer"
                            @click="isPwd = !isPwd" />
                    </template>
                </q-input>
                <q-btn unelevated color="primary" label="Login" no-caps />
            </div>
        </div>
        <div class="col-grow">
        </div>
    </div>
</template>
<script setup lang="ts">
import { ref } from 'vue';

const email = ref<string>('');
const password = ref<string>('');
const isPwd = ref<boolean>(true)
</script>
<style>
.login-container {
    height: 100vh;
}

.login-container .login-form {
    background-color: #fff;
    padding: 2rem 6rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
    height: 100%;
}

.header-login-form {
    display: flex;
    flex-direction: column;
    justify-content: center;
}

.header-login-form .header-login-form-label {
    font-size: xx-large;
    line-height: 25px;
    font-weight: 800;
}

.header-login-logo {
    width: 100px;
}

.form-input {
    display: flex;
    flex-direction: column;
    gap: 0.6rem;
}
</style>