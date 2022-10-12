
<template>
    <div class="icons">
        <div class="icon">
            <img :src="TerminalIcon" height="50" width="50" @dblclick="$emit('desktop-icon-click','terminal')" alt="" />
            <p>Portfolio</p>
        </div>
        <div class="icon">
            <a href="mailto:fahimaloy@gmail.com" class="icon">
                <img src="https://static2.sharepointonline.com/files/fabric/assets/brand-icons/product/svg/outlook_48x1.svg"
                    width="35" height="35" class="taskbarItem" alt="Word product icon" />
                <p>
                    Email Me
                </p>
            </a>
        </div>

        <!-- <div class="icon">
            <img :src="WordIcon" height="50" width="50" alt="" @click="alert_func('MS Word!')" />
            <p>Word</p>
        </div> -->
    </div>
</template>

<script setup>
import TerminalIcon from '../assets/terminal.svg'
import WordIcon from '../assets/word-app.svg'
let alert_func = (str) => {
    alert(`I am Working on ${str}. If you have any thoughts, then contact me.`)
}
</script>

<style scoped>
.icons {
    display: flex;
    flex-direction: column;

}

.icon {
    margin-top: 25px;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    cursor: pointer;
}

.icon p {
    line-height: 1px;
}

a {
    color: black;
    text-decoration: none;
}

.icon:first-child {
    margin-top: 1px;
}
</style>