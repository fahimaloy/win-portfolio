<script setup>
  import WelcomeIcon from '../assets/welcome-taskbar-icon.svg'
  import StartMenuIcon from '../assets/start-menu.svg'
  import SettingsIcon from '../assets/settings-gear-icon.svg'
  import WeatherIcon from '../assets/weather.svg'
  import TerminalIcon from '../assets/terminal.svg'
import { onMounted, ref, watch } from 'vue';
    let props = defineProps(['icon_list'])
    
  const currentTaskbarItems = [
    {
        id:'startmenuTaskbarIcon',
        icon: StartMenuIcon,
        func_param:'startMenu',
    },
    {
        id:'settingsTaskbarIcon',
        icon: SettingsIcon,
        func_param:'settings',

    },
    {
        id:'noteTaskbarIcon',
        icon: WelcomeIcon,
        func_param:'welcome',
        
    },
    {
        id:'weatherTaskbarIcon',
        icon: WeatherIcon,
        func_param:'weather',
        
    },
    {
        id:'terminalTaskbarIcon',
        icon:TerminalIcon,
        func_param:'terminal'
    }
]

</script>
<template>
    <div class="taskbar noselect">
        <div v-for="item in currentTaskbarItems" :key="item.id" class="taskbarIconWrapper" :id="item.id" @click="$emit('taskbar-icon-click',item.func_param)">
          <img :src="item.icon" width="35" height="35" class="taskbarItem" alt="Word product icon" />
          <div v-if="item.func_param == 'weather'" class="taskbarTemp">
         30°
        </div>
        </div>
        
        <div class="taskbarTime">
        </div>
      </div>
</template>