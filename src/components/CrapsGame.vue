<template>
  <div class="container">
    <div class="row">
      <div class="box bet-box col-sm">
        <h1>bet box</h1>
        <div>Bet: {{ bet }}</div>
        <div>Bank: {{ bank }}</div>
      </div>
      <div class="box roll-box col-sm">
        <h1>roll box</h1>
        <div class="row">
          <div class="die">{{ die1 }}</div>
          <div class="die">{{ die2 }}</div>

          <button class="roll-button" @click.prevent="rollDice">Roll Dice</button>
        </div>
        
      </div>
      <div class="box outcome-box col-sm">
        <h1>outcome box</h1>
        
        <div class="result">{{ message }}</div>

        <div class="point-box" v-if="point">Your Point is {{ point }}</div>

      </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        die1: 1,
        die2: 2,
        rollTotal: null,
        comeOut: true,
        message: "Roll!",
        point: null,
        bank: 500,
        bet: 0,
      }
    },
    methods: {
      rollDice() {
        this.die1 = null;
        this.die2 = null;

        let self = this;

        setTimeout(function() {
          self.die1 = Math.floor(Math.random() * 6) + 1;
          self.die2 = Math.floor(Math.random() * 6) + 1;
          self.rollTotal = self.die1 + self.die2;

          if(self.comeOut) {
            if(self.rollTotal===7 || self.rollTotal===11) {
              self.winLogic("You Win!");
            } else if(self.rollTotal===2 || self.rollTotal===3 || self.rollTotal===12) {
              self.loseLogic("Craps!");
            } else {
              self.pointLogic(self.rollTotal);
            }
          } else if(self.rollTotal===7) {
            self.loseLogic("7 out!");
          } else if (self.rollTotal===self.point) {
            self.winLogic("You hit your point!");
          } else {
            self.message = self.rollTotal;
          }
        }, 500);
      },
      winLogic(msg) {
        this.message = msg;
        this.comeOut = true;
      },
      loseLogic(msg) {
        this.message = msg;
        this.comeOut = true;
        this.point = null;
      },
      pointLogic(thePoint) {
        this.message = this.rollTotal + ", The point is " + this.rollTotal + "!";
        this.comeOut = false;
        this.point = thePoint;
      }

    }

  }
</script>

<style scoped>
  * {
    margin: 0px;
    padding: 0px;
  }

  .box {
    border: 1px solid black;
    height: 50vh;
  }

  .die {
    height: 4rem;
    width: 4rem;
    border: 1px solid black;
    border-radius: 5px;
    background-color: red;
    color: white;
    font-size: 2rem;
    line-height: 3rem;
    margin: 2rem auto;
  }

  .roll-button {
    width: 40%;
    height: 2rem;
    position: absolute;
    bottom: 0;
    left: 30%;
    right: 30%;
    margin: 1rem auto;
  }

  .result {
    margin-top: 4rem;
    font-size: 2rem;
  }

  .point-box {
    width: 40%;
    height: 2rem;
    position: absolute;
    bottom: 0;
    left: 30%;
    right: 30%;
    margin: 1rem auto;
  }


</style>
