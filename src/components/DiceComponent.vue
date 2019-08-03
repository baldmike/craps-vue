<template>
    <div class="row">
      <div class="box roll-box col-sm">
        <h1>ROLL BOX</h1>
        <div class="row">
          <div class="die">{{ dieOne }}</div>
          <div class="die">{{ dieTwo }}</div>

          

          <button class="roll-button" @click.prevent="rollDice">Roll Dice</button>

          
        </div>
      </div>
    </div>
</template>

<script>
  export default {
    data() {
      return {

      }
    },
    methods: {
      rollDice() {

        this.$store.dispatch('rollDice');

        let rollTotal = this.$store.state.rollTotal;

        console.log("ROLL TOTAL: " + rollTotal)

      },
      pointLogic(thePoint) {
        this.message = this.rollTotal + ", The point is " + this.rollTotal + "!";
        this.comeOut = false;
        this.point = thePoint;
      }
    },
    computed: {
        comeOut() {
          return this.$store.state.comeOut;
        },
        dieOne() {
          return this.$store.state.die1;
        },
        dieTwo() {
          return this.$store.state.die2;
        },
        rollAmount() {
            return this.$store.state.rollTotal;
        },
        rollTotal() {
            return this.$store.state.rollTotal;
        },
    }
  }
</script>

<style scoped>
  * {
    margin: 0px;
    padding: 0px;
  }

  .box {
    margin: 0px 40px;
    border: 1px solid black;
    height: 50vh;
    overflow: hidden;
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