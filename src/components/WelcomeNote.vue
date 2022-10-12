<script setup>

</script>
<template>
    <div class="panel note-panel" id="welcomenote" @mousedown="$emit('focus-window','welcome')" style="display:none;">
    <div class="header noselect">
      <span class="lightText"><i class="ms-Icon ms-Icon--QuickNoteSolid headerTitleIcon" aria-hidden="true"></i><span class="headerTitleText"> Welcome</span></span>
      <div class="headerIcons">
        <i class="ms-Icon ms-Icon--ChromeMinimize" id="welcomeMinimize" aria-hidden="true" @click="$emit('minimize-window','welcome')"></i>
        <i class="ms-Icon ms-Icon--ChromeRestore" aria-hidden="true"></i>
        <i class="ms-Icon ms-Icon--ChromeClose" id="welcomeClose" aria-hidden="true" @click="$emit('close-window','welcome')"></i>
      </div>
    </div>
    <div class="panel-body" id="panelBody">
      <div class="headerImage parallax noselect" data-depth=".1" id="headerImage">
        <div class="headerImageOverlay">
          <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="50px" height="50px" viewBox="0 0 443.704 443.704" version="1.1">
            <g id="surface1">
              <path style=" stroke:none;fill-rule:nonzero;fill:rgb(100%,100%,100%);fill-opacity:1;" d="M 227.570313 307.621094 L 227.570313 387.675781 L 387.675781 387.675781 L 387.675781 227.570313 L 227.570313 227.570313 Z M 56.03125 307.621094 L 56.03125 387.675781 L 216.132813 387.675781 L 216.132813 227.570313 L 56.03125 227.570313 Z M 227.570313 136.082031 L 227.570313 216.132813 L 387.675781 216.132813 L 387.675781 56.03125 L 227.570313 56.03125 Z M 56.03125 136.082031 L 56.03125 216.132813 L 216.132813 216.132813 L 216.132813 56.03125 L 56.03125 56.03125 Z M 56.03125 136.082031 " />
            </g>
          </svg>
          &nbsp;Windows 11
        </div>
      </div>
      <div class="noteBodyText">
        <p>Welcome to my build of the Windows 11 UI. I tried my best to recreate the Windows 11 UI based on the Fluent Design documentation and the recently released Windows 11 preview video. At the time of making this, that's all I had to go off. I'm curious to see how far I missed the mark once Windows 11 is publicly available. Have fun and play around!</p>
        <p>Here are some things you can explore:</p>
        <ul>
          <li>
            Check the weather by clicking the cloud in the taskbar
          </li>
          <li>
            Open the Windows start menu
          </li>
          <li>
            Drag windows around, close them, minimize them. Window states will update, z-indexes will update, windows will animate in and out depending on if you're restoring the window, closing the window, or minimizing the window.
          </li>
          <li>
            COMING SOON: Shut the computer down in the start menu
          </li>
          <li>
            COMING SOON: Open the settings from the taskbar and switch to a dark theme
          </li>
          <li>
            TO DO: Polish! It could use some buffing around the edges to get it more in-line with Fluent Design.
          </li>
          <li>
            TO DO: Clean-up code. It's a mess. I'll need to do this before I get dark / light mode working.
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>