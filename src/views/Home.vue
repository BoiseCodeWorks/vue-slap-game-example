<template>
  <div class="home row">
    <div class="col-12">
      <h1>{{target.name}}</h1>
      <h3 :class="healthStatus()" v-if="target.health > 0">Health: {{target.health}}</h3>
      <h3 v-if="target.health == 0">It's dead Jim</h3>
      <h3>Hits: {{target.hits}}</h3>
      <button class="btn btn-danger" @click="attackShip(attack)"
        v-for="attack in target.attacks">{{attack.name}}</button>
      <button @click="reset" class="btn btn-success">Reset</button>
    </div>
  </div>
</template>

<script>

  export default {
    name: 'home',
    props: ["target"],
    data() {
      return {

      }
    },
    methods: {
      attackShip(atk) {
        this.target.health -= atk.dmg
        this.target.hits++
        if (this.target.health < 0) {
          this.target.health = 0
        }
      },
      healthStatus() {
        let output = "red"
        if (this.target.health >= 90) {
          output = 'green'
        }
        else if (this.target.health >= 70) {
          output = 'yellow'
        }
        else if (this.target.health >= 50) {
          output = 'orangered'
        }
        return output
      },
      reset() {
        this.target.health = 100
        this.target.hits = 0
      }
    }
  }
</script>


<style>
  .green {
    color: green;
  }

  .red {
    color: red;
  }

  .orangered {
    color: orangered;
  }

  .yellow {
    color: yellow;
  }

  h1 {
    color: red;
  }
</style>