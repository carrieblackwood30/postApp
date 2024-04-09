<template>
    <div class="regContainer">
        <span>login:</span>
        <button @click="loginContainerDisplay">
            <img src="https://www.svgrepo.com/show/44183/male-user.svg" alt="" width="20">
        </button>
    </div>

    <div class="formContainer" :class="`FormDisplay-${loginContainer ? 'off' : 'on'}`" @click.self="loginContainer = false">
        <form action="" class="login"  :class="`display-${display ? 'off' : 'on'}`" @submit.prevent="onSubmit">
            <h3>login</h3>
            <input type="text" placeholder="login.." required >
            <input type="password" placeholder="password.." autocomplete="on" required>
            <button>submit</button>
            <p style="font-size: 1rem;">don't have an account? <br>
                click here: <button type="button" @click="switchToRegistration">registration</button></p>
        </form>
        <form action="" class="registration" :class="`display-${display ? 'on' : 'off'}`" @submit.prevent="onSubmit">
            <h3>registration</h3>
            <input type="text" placeholder="login..." v-model="loginFromRegistration" required>
            <input type="password" placeholder="password..." autocomplete="on" v-model="passwordFromRegistration" required>
            <button @click="registrationBtn">submit</button>
            <p style="font-size: 1rem;">if you have an account<br>
                click here: <button type="button" @click="switchToRegistration">registration</button></p>
        </form>
    </div>
</template>

<script setup>
import { ref } from "vue";

    const display = ref(false)
    const loginContainer = ref(false)

    const loginFromRegistration = ref('')
    const passwordFromRegistration = ref('')

    function switchToRegistration(){
        return display.value = !display.value
    }

    function loginContainerDisplay(){
        return loginContainer.value = !loginContainer.value
    }

    function registrationBtn(){

        const userData = []
        userData.push({name: loginFromRegistration.value, password: passwordFromRegistration.value})
        console.log(userData)
        localStorage.setItem("user", JSON.stringify(userData))

        loginFromRegistration.value = ' '
        passwordFromRegistration.value = ' '
        loginContainer.value = !loginContainer.value
    }

</script>

<style scoped>
    .formContainer{
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, .5);
        z-index: 20;
        transition: .3s all;
        display: flex;
        align-items: center;
        justify-content: center;
        display: none;
    }

    .formContainer form{
        background-color: #fff;
        border-radius: 10px;
        color: #666;
        display: flex;
        flex-direction: column;
        gap: 1.2rem;
        padding: 1.2rem;
    }

    .formContainer .display-on{
        display: none;
    }

    .formContainer .display-off{
        display: flex;
    }

    .FormDisplay-off{
        display: flex;
    }

    .FormDisplay-on{
        display: none;
    }

</style>