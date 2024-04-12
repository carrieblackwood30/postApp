<template>
    <div class="createBtn">
        <h3>create post: <button>+</button></h3>
        <div class="createPostContainer">

            <form action="" @submit.prevent="onSubmit">
                <button style="margin-left: auto;">x</button>
                <label for="title">титулка:</label>
                <input type="text" id="title" placeholder="титулка...">
                <label for="header">заголовок:</label>
                <input type="text" id="header" placeholder="титулка...">
                <label for="post"></label>
                <div class="buttonContainer">
                    <button :class="`clicked-button-${clickedButtonItalic ? 'on' : 'off'}`" @click="italic = !italic; clickedButtonItalic = !clickedButtonItalic">italic</button>
                    <button :class="`clicked-button-${clickedButtonBold ? 'on' : 'off'}`" @click="clickedButtonBold = !clickedButtonBold; bold = !bold">bold</button>
                    <button :class="`clicked-button-${clickedButtonUnderline ? 'on' : 'off'}`" @click="clickedButtonUnderline = !clickedButtonUnderline; underline = !underline">underline</button>
                    <label for="color">color pick:</label>
                    <input v-model="color" type="color">
                    <div class="font-size">
                        <button>+</button>
                        <span>font size</span>
                        <button>-</button>
                    </div>
                </div>
                <textarea :class="`style-italic-${italic ? 'on' : 'off'} style-bold-${bold ? 'on' : 'off'} style-underline-${underline ? 'on' : 'off'}`" cols="30" rows="10" style="resize: none; height: 80%;" :style="`color: ${color};`"></textarea>
                <button style="width: fit-content; margin-left: auto;">отправить</button>
            </form>

        </div>
    </div>
</template>

<script setup>
import { ref, watch } from "vue";

const italic = ref(false)
const bold = ref('')
const underline = ref('')

const clickedButtonItalic = ref(false)
const clickedButtonBold = ref(false)
const clickedButtonUnderline = ref(false)

const color = ref('')
console.log(color.value)

</script>

<style scoped>
.createBtn{
    display: flex;
    width: 100%;
    justify-content: center;
    margin: 1rem;
}

.createBtn button{
    height: 30px;
    padding: 0 1rem;
    border-radius: 10px;
}

.createPostContainer{
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
}

.createPostContainer input{
    height: 40px;
}

.buttonContainer{
    display: flex;
    gap: 1rem;
    align-items: center;
    justify-content: center;   
}

.buttonContainer button{
    width: fit-content;
    border: none;
} 

.createPostContainer form{
        background-color: #fff;
        border-radius: 10px;
        color: #666;
        display: flex;
        flex-direction: column;
        gap: 1.2rem;
        padding: 1.2rem;
        width: 80vw;
        height: 80vh;
}

.clicked-button-on{
    background-color: var(--secondary-color);
}

.style-italic-on{
    font-style: italic;
}

.style-bold-on{
    font-weight: bold;
}

.style-underline-on{
    text-decoration: underline;
}

</style>