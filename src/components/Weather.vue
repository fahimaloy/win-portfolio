<script setup>
import { onMounted, reactive } from '@vue/runtime-core'
import WeatherIcon from '../assets/weather.svg'
import axios from 'axios'
let weatherData = reactive([{
  longitude:0,
  latitude:0,
  currentConditions:{
    temp:0,
    conditions:'',
  }
}])
onMounted(()=>{
  axios.get('http://ipwho.is/').then((data)=>{
    let link = `https://weather.visualcrossing.com/VisualCrossingWebServices/rest/services/timeline/${data.data.city}?unitGroup=metric&key=8NTTEUKMK668BMUYD9KYR2736&contentType=json`
    axios.get(link).then((wData)=>{
      weatherData[0]=wData.data
    })
  })
})

</script>
<template>
    <div class="panel weatherPanel" @mousedown="$emit('focus-window','weather')" style="display:none;" id="weatherPanel">
          <div class="header noselect" style="display:flex; justify-content:space-between">

            <div style="display:flex; align-items:center; justify-content:space-around"><img :src="WeatherIcon" height="25" width="25" style="margin-left:10px;" alt=""><span class="headerTitleText"> Weather</span></div>
            <div class="headerIcons">
              
              <i class="ms-Icon ms-Icon--ChromeMinimize" id="welcomeMinimize" aria-hidden="true" @click="$emit('minimize-window','weather')"></i>
              <i class="ms-Icon ms-Icon--ChromeClose" id="welcomeClose" aria-hidden="true" @click="$emit('close-window','weather')"></i>
            </div>
          </div>
          <div class="panel-inner">
            <div class="panel-left">
              <div class="panel-left-highlow-text">
                Longitude {{weatherData[0].longitude}} <br />
                Latitude {{weatherData[0].latitude}}                 
              </div>
              <div class="panel-left-locationdate-text">
                {{weatherData[0].timezone}}
              </div>
              <div class="panel-left-day">
                Sunrise {{weatherData[0].currentConditions.sunrise}} <i class="ms-Icon ms-Icon--Sunny" aria-hidden="true"></i>
              </div>
              <div class="panel-left-day">
                Sunset {{weatherData[0].currentConditions.sunset}} <i class="ms-Icon ms-Icon--Rain" aria-hidden="true"></i>
              </div>
              <div class="panel-left-day">
                Humidity {{weatherData[0].currentConditions.humidity}} <i class="ms-Icon ms-Icon--Fog" aria-hidden="true"></i>
              </div>
            </div>
          </div>
          <div class="panel-right">
            <div class="weatherTemperature">{{weatherData[0].currentConditions.temp}}° C<br /><small>{{weatherData[0].currentConditions.conditions}}</small></div>
          </div>
          <div class="cloud">
          </div>
          
          
        </div>
</template>