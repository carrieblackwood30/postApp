<template>

    <div class="postsContainer" style="width: 100%;">
        <div class="createBtn">
        <h3>create post: <button @click.prevent="createPostDisplay = !createPostDisplay">+</button></h3>
        
        <div class="createPostContainer" :class="`createPostDisplay-${createPostDisplay ? 'on' : 'off'}`">

            <form action="" @submit.prevent="onSubmit">
                <button style="margin-left: auto;"  @click.prevent="createPostDisplay = !createPostDisplay">x</button>
                <label for="title">титулка:</label>
                <input type="text" id="title" placeholder="титулка..." v-model="titlePost">
                <label for="header">заголовок:</label>
                <input type="text" id="header" placeholder="заголовок..." v-model="headerPost">
                <label for="post"></label>
                <div class="buttonContainer">
                    <button :class="`clicked-button-${clickedButtonItalic ? 'on' : 'off'}`" @click="italic = !italic; clickedButtonItalic = !clickedButtonItalic">italic</button>
                    <button :class="`clicked-button-${clickedButtonBold ? 'on' : 'off'}`" @click="clickedButtonBold = !clickedButtonBold; bold = !bold">bold</button>
                    <button :class="`clicked-button-${clickedButtonUnderline ? 'on' : 'off'}`" @click="clickedButtonUnderline = !clickedButtonUnderline; underline = !underline">underline</button>
                    <label for="color">color pick:</label>
                    <input v-model="color" type="color">
                    <div class="font-size">
                        <button @click="fontSize += .5">+</button>
                        <span>font size</span>
                        <button @click="fontSize -= .5">-</button>
                    </div>
                </div>
                <textarea v-model="textareaPost" :class="`style-italic-${italic ? 'on' : 'off'} style-bold-${bold ? 'on' : 'off'} style-underline-${underline ? 'on' : 'off'}`" cols="30" rows="10" style="resize: none; height: 80%;" :style="`color: ${color}; font-size: ${fontSize}rem;`"></textarea>
                <button style="width: fit-content; margin-left: auto;" @click="addPost">отправить</button>
            </form>

        </div>
    </div>

    <div class="posts" v-for="post in posts" :key="post">
            <div class="post">
                <h3>{{ post.title }}</h3>
                <p>{{ post.header }}</p>
                <h4>{{ post.textarea }}</h4>
            </div>
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
const fontSize = ref(1)

const createPostDisplay = ref(false)

const titlePost = ref('')
const headerPost = ref('')
const textareaPost = ref('')

const posts = ref([])

function addPost(){
    posts.value.push({
        title: titlePost.value,
        header: headerPost.value,
        textarea: textareaPost.value
    })

    titlePost.value = ''
    headerPost.value = ''
    textareaPost.value = ''

    createPostDisplay.value = !createPostDisplay

}

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

.createPostDisplay-off{
    display: none;
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

.posts{
    display: flex;
    width: 100%;
}

</style>