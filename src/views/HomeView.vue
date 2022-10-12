<script setup>
import { onMounted } from "@vue/runtime-core";
import WindowsMenu from "../components/WindowsMenu.vue";
import Settings from "../components/Settings.vue";
import TaskBar from "../components/TaskBar.vue";
import WelcomeNote from "../components/WelcomeNote.vue";
import DesktopIcons from "../components/DesktopIcons.vue";
import Terminal from "../components/Terminal.vue";
import Weather from "../components/Weather.vue";
import TerminalIcon from '../assets/terminal.svg'
import { reactive } from "vue";

  const windows = [
    {
      name: "welcome",
      isOpen: false,
      isMinimized: false,
      hasFocus: false,
      taskbarid: "#noteTaskbarIcon",
      taskbarindicator: "#noteTaskbarIndicator",
      windowid: "#welcomenote"
    },
    {
      name: "settings",
      isOpen: false,
      isMinimized: false,
      hasFocus: false,
      taskbarid: "#settingsTaskbarIcon",
      taskbarindicator: "#settingsTaskbarIndicator",
      windowid: "#settingswindow"
    },
    {
      name: "weather",
      isOpen: false,
      isMinimized: false,
      hasFocus: false,
      taskbarid: "#weatherTaskbarIcon",
      taskbarindicator: "#weatherTaskbarIndicator",
      windowid: "#weatherPanel"
    },
    {
      name: "startMenu",
      isOpen: false,
      isMinimized: false,
      hasFocus: false,
      taskbarid: "#startmenuTaskbarIcon",
      taskbarindicator: "",
      windowid: "#startMenuPanel"
    },
    {
      name: "terminal",
      isOpen: false,
      isMinimized: false,
      hasFocus: false,
      taskbarid: "#terminalTaskbarIcon",
      taskbarindicator: "",
      windowid: "#terminalPanel",
      
    }
  ];

let  taskbarIconIDList = reactive([
      'startmenuTaskbarIcon',
      'settingsTaskbarIcon',
      'noteTaskbarIcon',
      'weatherTaskbarIcon',

    ])
  
  
  var openedWindows = [];

  function UpdateTaskBar(){
    //Remove the focus state from all windows
    for(var i = 0; i < windows.length; i++){
      windows[i].hasFocus = false;
    }
    
    //apply focus state on last openedwindow
    if(openedWindows.length > 0){
      openedWindows[openedWindows.length - 1].hasFocus = true;
    }
    
    for(var i = 0; i < windows.length; i++){
      $(windows[i].taskbarid).removeClass();
      $(windows[i].taskbarid).addClass("taskbarIconWrapper");
      
      if(windows[i].isOpen){
        $(windows[i].taskbarid).addClass("active");
        $(windows[i].taskbarindicator).removeClass("unfocused");
        
        if(windows[i].hasFocus){
          $(windows[i].taskbarindicator).show();
          $(windows[i].taskbarid).addClass("focused");
        }
        if(windows[i].isMinimized){
          $(windows[i].taskbarindicator).show();
          $(windows[i].taskbarindicator).addClass("unfocused");
        }
      }
      else{
        $(windows[i].taskbarindicator).addClass("unfocused");
        $(windows[i].taskbarindicator).hide();
      }
    }
  }
  function UpdateZIndex(){
    for(var i = 0; i < openedWindows.length; i++){
      for(var j = 0; j < 4; j++){
        $(openedWindows[i].windowid).removeClass("zindex" + j);
      }
      $(openedWindows[i].windowid).addClass("zindex" + i);
    }
  }
  function FocusWindow(windowToFocus){
    var objectarr = windows.filter(obj => {
      return obj.name === windowToFocus
    });
    
    var object = objectarr[0];
    //Focus Window
    object.isOpen = true;
    object.isMinimized = false;
    object.hasFocus = true;
    //remove item from openedwindows array
    openedWindows = openedWindows.filter(function( obj ) {
      return obj.name !== object.name;
    });
    //and puts it at the back
    openedWindows.push(object);
    UpdateTaskBar();
    UpdateZIndex();
    
  }
  function TaskbarIconClick(clickedIcon){
    var objectarr = windows.filter(obj => {
      return obj.name === clickedIcon
    });
    if(clickedIcon == 'terminal'){
      taskbarIconIDList.push('terminalTaskbarIcon')
      console.log(taskbarIconIDList);
    }
    var object = objectarr[0];
    
    if(object.name == "startMenu"){
      if(object.isOpen){
        //Close Window
        $(object.windowid).toggle("drop", { direction: "down" });
        object.isOpen = false;
        object.isMinimized = false;
        object.hasFocus = false;
        //remove item from openedwindows array
        openedWindows.pop();
      }
      else{
        //Open window
        $(object.windowid).toggle("drop", { direction: "down" });
        object.isOpen = true;
        object.isMinimized = false;
        object.hasFocus = true;
        //put item at end of openedwindows array
        openedWindows.push(object);
      }
    }
    else{
      //If the start menu is open, close it
      if(windows[3].isOpen){
        //Close Window
        $(windows[3].windowid).toggle("drop", { direction: "down" });
        windows[3].isOpen = false;
        windows[3].isMinimized = false;
        windows[3].hasFocus = false;
        //remove item from openedwindows array
        openedWindows.pop();
      }
      if(object.isOpen){
        if(object.isMinimized){
          //Restore Window
          $(object.windowid).toggle("drop", { direction: "down" });
          object.isOpen = true;
          object.isMinimized = false;
          object.hasFocus = true;
          //put item at end of openedwindows array
          openedWindows.push(object);
        }
        else{
          if(object.hasFocus){
            //Minimize Window
            $(object.windowid).effect("drop", { direction: "down" });
            object.isOpen = true;
            object.isMinimized = true;
            object.hasFocus = false;
            //remove item from openedwindows array
            openedWindows = openedWindows.filter(function( obj ) {
                return obj.name !== object.name;
            });
          }
          else{
            //Focus Window
            object.isOpen = true;
            object.isMinimized = false;
            object.hasFocus = true;
            //remove item from openedwindows array
            openedWindows = openedWindows.filter(function( obj ) {
                return obj.name !== object.name;
            });
            //and puts it at the back
            openedWindows.push(object);
          }
        }
      }
      else{
        //Open window
          $(object.windowid).toggle("fade");
          object.isOpen = true;
          object.isMinimized = false;
          object.hasFocus = true;
          //put item at end of openedwindows array
          openedWindows.push(object);
      }
    }
    UpdateTaskBar();
    UpdateZIndex();
  }
  let datetime = ''
  function GetTime(){
    var date = new Date();
    var today = formatAMPM(date);
    var month = date.getMonth();
    month += 1;
    var calDate =
      month.toString() +
      "/" +
      date.getDate().toString() +
      "/" +
      date.getFullYear();
  
    $(".taskbarTime").html(today + "<br />" + calDate);
  }
  
  function formatAMPM(date) {
    var hours = date.getHours();
    var minutes = date.getMinutes();
    var ampm = hours >= 12 ? "pm" : "am";
    hours = hours % 12;
    hours = hours ? hours : 12; // the hour '0' should be '12'
    minutes = minutes < 10 ? "0" + minutes : minutes;
    var strTime = hours + ":" + minutes + " " + ampm;
    return strTime;
  }
  
  function updateTime() {
    setTimeout(function () {
      GetTime();
      updateTime();
    }, 60000);
  }
  onMounted(()=>{

    GetTime();
     UpdateTaskBar();
    UpdateZIndex();
    updateTime();
  })
  function CloseWindow(windowToClose){
    var objectarr = windows.filter(obj => {
      return obj.name === windowToClose
    });
    var object = objectarr[0];
    //Close Window
    $(object.windowid).toggle("fade");
    object.isOpen = false;
    object.isMinimized = false;
    object.hasFocus = false;
    //remove item from openedwindows array
    openedWindows = openedWindows.filter(function( obj ) {
      return obj.name !== object.name;
    });
    UpdateTaskBar();
    UpdateZIndex();
  }
  
  
let MinimizeWindow = (windowToClose)=>{
    var objectarr = windows.filter(obj => {
      return obj.name === windowToClose
    });
    var object = objectarr[0];
    console.log("1"+object)
    //MinimizeWindow
    $(object.windowid).effect("drop", { direction: "down" });
    object.isOpen = true;
    object.isMinimized = true;
    object.hasFocus = false;
    //remove item from openedwindows array
    openedWindows = openedWindows.filter(function( obj ) {
      return obj.name !== object.name;
    });
    UpdateTaskBar();
    UpdateZIndex();
    console.log("2"+object)
  }

</script>

<template>
  <main>
    <div class="container">
      <div class="desktop-icons">
        <Terminal @focus-window="FocusWindow" @minimize-window="MinimizeWindow" @close-window="CloseWindow" />
        <DesktopIcons @desktop-icon-click="TaskbarIconClick" />
      </div>
        <!-- <iframe src="http://fahimaloy.herokuapp.com/"
            width="98%"
            height="550px"></iframe> -->
          <WindowsMenu />
          <Weather @focus-window="FocusWindow" @minimize-window="MinimizeWindow" @close-window="CloseWindow"/>
          <Settings @focus-window="FocusWindow" @minimize-window="MinimizeWindow" @close-window="CloseWindow"/>
          <WelcomeNote @focus-window="FocusWindow" @minimize-window="MinimizeWindow" @close-window="CloseWindow" />

      </div>
      
      <TaskBar :icon_list="taskbarIconIDList" @taskbar-icon-click="TaskbarIconClick" />
  </main>
</template>
<style scoped>
.desktop-icons{
  position: absolute;
  top:1px;
  left:10px;
}
</style>