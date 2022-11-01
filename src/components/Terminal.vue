<script setup></script>
<template>
  <div
    class="panel weatherPanel"
    @mousedown="$emit('focus-window', 'terminal')"
    style="display: none"
    id="terminalPanel"
  >
    <div
      class="header noselect"
      style="display: flex; justify-content: space-between"
    >
      <div
        style="
          display: flex;
          align-items: center;
          justify-content: space-around;
        "
      >
        <img
          src="/P001.jpeg"
          height="25"
          width="25"
          style="margin-left: 10px"
          alt=""
        /><span class="headerTitleText"> PortFolio</span>
      </div>
      <div class="headerIcons">
        <i
          class="ms-Icon ms-Icon--ChromeMinimize"
          id="welcomeMinimize"
          aria-hidden="true"
          @click="$emit('minimize-window', 'terminal')"
        ></i>
        <i
          class="ms-Icon ms-Icon--ChromeClose"
          id="welcomeClose"
          aria-hidden="true"
          @click="$emit('close-window', 'terminal')"
        ></i>
      </div>
    </div>
    <div class="panel-inner">
      <iframe
        src="https://fahimaloy-terminal-portfolio.onrender.com/"
        width="98%"
        height="650px"
      ></iframe>
    </div>
  </div>
</template>
