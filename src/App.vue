<template>
  <div id="app">
    <!-- <craps-game/> -->
    <div class="container">
      <div class="row">
        <div class="col-sm">
          <wager-component/>
        </div>
        
        <div class="col-sm">
          <dice-component/>
        </div>
        
        <div class="col-sm">
          <outcome-component/>
        </div>
      </div>
      <div class="row">
        <div class="col-sm">
          <now-playing/>
        </div>
      </div>
    </div>
    

  </div>
</template>

<script>
import CrapsGame from './components/CrapsGame.vue'

import WagerComponent from './components/WagerComponent.vue'
import DiceComponent from './components/DiceComponent.vue'
import OutcomeComponent from './components/OutcomeComponent.vue'
import NowPlaying from './components/NowPlayingComponent.vue'

export default {
  name: 'app',
  components: {
    CrapsGame,
    WagerComponent,
    DiceComponent,
    OutcomeComponent,
    NowPlaying
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
