<template>
<div class="container">
  <div class="row">
      <div class="box bet-box col-sm">
        <h1>bet box</h1>
        <div>Bet: {{ bet }}</div>
        <div>Bank: {{ bank }}</div>
        <div class="row">
          <div class="chip chip5">5</div>
          <div class="chip chip25">25</div>
          <div class="chip chip50">50</div>
          <div class="chip chip100">100</div>
        </div>
      </div>
      
    </div>

    
</div>
    
</template>

<script>
  export default {
    data() {
      return {
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

  .chip {
    height: 50px;
    width: 50px;
    border-radius: 50%;
    margin-left: auto;
    margin-right: auto;
    color: white;
    line-height: 3rem;
  }

  .chip5 {
    height: 50px;
    width: 50px;
    background: red;
    border-radius: 50%
  }

  .chip25 {
    background: blue;
  }

  .chip50 {
    background: green;
  }

  .chip100 {
    background: black;
  }



</style>
