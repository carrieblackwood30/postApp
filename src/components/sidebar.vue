<template>

    <div class="sidebar">
        <div class="userContainer">
            <h3 :style="randomColor" style="text-transform: uppercase;">{{ userFirstLetter }}</h3>
            <div class="userInformation">
                <p v-if="user() != 'User login = null'" style="font-size: 1rem; color: whitesmoke ;">{{ user() }}</p>
                <p style="color: whitesmoke;">User id: 0</p>
            </div>
        </div>
    </div>
    
</template>

<script setup>
import { ref, watch } from "vue"

    const user = ref(() => {
        const userLogin = JSON.parse(localStorage.getItem(("user")))

        if (userLogin != null) {
            return userLogin[0].name
        }else return 'User login = null'
    })

    console.log(user.value())

    const userFirstLetter = user.value()[0]
    const randomColor = `background-color: rgb(${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)}, ${Math.floor(Math.random() * 255)})`

</script>

<style scoped>

.sidebar{
    background-color: var(--secondary-color);
    width: 20%;
    height: 74.4vh;
    padding: 4px;
}

.userContainer{
    display: flex;
    gap: .8rem;
    padding: .4rem;
}

.sidebar .userContainer h3{
    border: 2px solid;
    border-radius: 50%;
    padding: .1rem;
    font-size: 2rem;
    width: 40px;
    height: 40px;
    text-align: center;
}

</style>