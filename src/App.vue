<template>
  <div id="app">
    <div id="background"></div>
    <LogoComponent img='../assets/logo-white.png'/>
    <HeaderComponent h1="Watchdoor"/>
    <LoginFormComponent></LoginFormComponent>
  </div>
</template>

<script>
import LogoComponent from './components/LogoComponent.vue'
import HeaderComponent from './components/HeaderComponent.vue'
import LoginFormComponent from './components/LoginFormComponent.vue'

export default {
  name: 'App',
  components: {
    LogoComponent,
    HeaderComponent,
    LoginFormComponent

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  display: grid;
  grid-template-rows: 15em auto 1fr;
}

#background {
  position: absolute;
  top:0%;
  left: 0;
  height: 100%;
  min-height: 700px;
  width: 100%;
  background: #F6AE2D;
  z-index: -1;
  clip-path: polygon(100% 0, 100% 79%, 0 100%, 0 0);
}

body {
  margin: 0;
}

@media only screen and (min-width: 768px) {
  #background {
    clip-path: polygon(100% 0, 100% 67%, 50% 100%, 0 100%, 0 0);
  }
}
</style>
