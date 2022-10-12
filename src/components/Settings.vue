<script setup>
    
</script>
<template>
    <div class="panel settingsPanel" id="settingswindow" @mousedown="$emit('focus-window','settings')" style="display:none;">
          <div class="header noselect">
            <span class="lightText"><i class="ms-Icon ms-Icon--Settings headerTitleIcon" aria-hidden="true"></i><span class="headerTitleText"> Settings</span></span>
            <div class="headerIcons">
              <i class="ms-Icon ms-Icon--ChromeMinimize" id="welcomeMinimize" aria-hidden="true" @click="$emit('minimize-window','settings')"></i>
              <i class="ms-Icon ms-Icon--ChromeRestore" aria-hidden="true"></i>
              <i class="ms-Icon ms-Icon--ChromeClose" id="welcomeClose" aria-hidden="true" @click="$emit('close-window','settings')"></i>
            </div>
          </div>
          <div class="panel-body settingsPanelBody noselect" id="panelBody">
            <div class="settingsProfileRow">
              <div class="profilePicture-settings">
              </div>
              <div class="settingsName">
                Fahim Ahmed <br /> <small class="lightText">fahimaloy@gmail.com</small>
              </div>
            </div>
      
            <div class="settingsLeftColumn">
              <div class="settingsItem active">
                <i class="ms-Icon ms-Icon--System" aria-hidden="true"></i> System
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--InternetSharing" aria-hidden="true"></i> Bluetooth
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--Globe" aria-hidden="true"></i> Network & internet
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--Brush" aria-hidden="true"></i> Personalization
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--AppIconDefaultAdd" aria-hidden="true"></i> Apps
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--People" aria-hidden="true"></i> Account
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--Clock" aria-hidden="true"></i> Time & language
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--Game" aria-hidden="true"></i> Gaming
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--EaseOfAccess" aria-hidden="true"></i> Accessibility
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--Shield" aria-hidden="true"></i> Privacy & security
              </div>
              <div class="settingsItem">
                <i class="ms-Icon ms-Icon--Sync" aria-hidden="true"></i> Windows update
              </div>
            </div>
            <div class="settingsRightColumn">
              <div class="themePreview">
              </div>
              <div class="themeSelect">
                Select a theme to apply
                <div class="lightThemePick active">
                </div>
                <div class="darkThemePick">
                </div>
              </div>
              <div class="settingsOptions">
                <div class="settingsSystemOption">
                  <i class="ms-Icon ms-Icon--PhotoCollection systemIcon" aria-hidden="true"></i>
                  <div class="settingsSystemOptionText">
                    Background <br />
                    <small class="lightText">Background image, color, slideshow</small>
                  </div>
                </div>
                <div class="settingsSystemOption">
                  <i class="ms-Icon ms-Icon--Color systemIcon" aria-hidden="true"></i>
                  <div class="settingsSystemOptionText">
                    Colors <br />
                    <small class="lightText">Background image, color, slideshow</small>
                  </div>
                </div>
                <div class="settingsSystemOption">
                  <i class="ms-Icon ms-Icon--Lock systemIcon" aria-hidden="true"></i>
                  <div class="settingsSystemOptionText">
                    Themes <br />
                    <small class="lightText">Background image, color, slideshow</small>
                  </div>
                </div>
                <div class="settingsSystemOption">
                  <i class="ms-Icon ms-Icon--PhotoCollection systemIcon" aria-hidden="true"></i>
                  <div class="settingsSystemOptionText">
                    Themes <br />
                    <small class="lightText">Background image, color, slideshow</small>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
</template>