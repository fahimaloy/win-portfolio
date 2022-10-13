<script setup>
import HomeView from './views/HomeView.vue';
import Loading from './components/Loading.vue';
import { onMounted ,ref } from '@vue/runtime-core';

let isContextMenuOpen = false
let openCustomContextMenu=(e)=>{
    console.log("Custom Context Menu")
    isContextMenuOpen = true
}
let loading = ref(true)
let elem = document.getElementById("app");
function openFullscreen() {
  if (elem.requestFullscreen) {
    elem.requestFullscreen();
  } else if (elem.webkitRequestFullscreen) { /* Safari */
    elem.webkitRequestFullscreen();
  } else if (elem.msRequestFullscreen) { /* IE11 */
    elem.msRequestFullscreen();
  }
}

onMounted(()=>{
    
    setTimeout(()=>{
        loading.value=false
    },5000)
})
</script>

<template>
<Loading  v-if="loading" /> 
<!-- <button style="position:absolute;top:999999px;" id="fullscreenbutton" @click="openFullscreen" v-if="loading"></button> -->
<HomeView @mousemoveh="openFullscreen" v-else @contextmenu.prevent="openCustomContextMenu"/>
</template>

