<template>
  <div id="app" class="container">
    <div class="card has-background-light is-flex-mobile">
      <header class="card-header">
        <h2 class="title is-2 is-medium is-primary is-bold  has-text-info">Caluladora de swag</h2>
      </header>
      <div class="card-content">
        <form @submit.prevent>
          <div class="control">
            <div class="field">
              <label class="label"> Edad </label>
              <input type="number" class="input" v-model.trim="age">
            </div>
          </div>
          <div>
            <label class="label"> Sexo </label>
            <input type="radio" name="gender" value="Macho" v-model='sex'> Macho 
            <input type="radio" name="gender" value="Hembra" v-model='sex'> Hembra
          </div>
          <label class="label"> Estatura (metros) </label>
          <input type="number" min="0" step="0.01" v-model="height" class="input">
          <label class="label" v-if="sex=='Macho'">
            <p> Talla de zapato </p>
            <input type="number" min="0"  v-model="footSize" class="input">
          </label>
          <label class="label" v-else>
            <p>Talla de sujetador</p>
            <input type="number" min="60" step="5" v-model="braSize" @keyup="makeAlert" class="input">
          </label>
          <input type="submit" value="plop" class="button"> </input>
        </form>
      </div>
    </div>
  </div>
</template>


<script>

export default {

  name: "app",

  data() {
    return {
      age: "18",
      height: "1.65",
      sex: "Macho", 
      footSize: "40",
      braSize: "80",
      isAlert: false,
    };
  },

  methods: {
    makeAlert() {
      this.isAlert = true;
    }
  },

  computed: {
      totalValue() {
        return this.age +  this.height*20 + this.footSize + this.braSize
      }
  },

};

</script>


<style>

  .alert {
    background-color: red;
  }
  body {
    padding-top: 50px;
    padding-left: 50px;
  }
  div .card {
    max-width: 500px;
  }
  header {
    padding-left: 20px;
  }

</style>
