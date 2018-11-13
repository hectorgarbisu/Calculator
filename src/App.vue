<template>
  <div id="app">
    <h2>Caluladora de swag</h2>
    <form @submit.prevent="makeAlert">
      <p>Edad</p><input type="number" v-model.trim="age">
      <p>Sexo</p>
        <input type="radio" name="gender" value="Macho" v-model='sex'> Macho 
        <input type="radio" name="gender" value="Hembra" v-model='sex'> Hembra
      <p>Estatura (metros)</p>
      <input type="number" min="0" step="0.01" v-model="height">
      <div v-if="sex=='Macho'">
        <p>Talla de zapato</p>
        <input type="number" min="0"  v-model="footSize">
      </div>
      <div v-else>
        <p>Talla de sujetador</p>
        <input type="number" min="60" step="5" v-model="braSize" @keyup="makeAlert">
      </div>
    </form>

    {{ totalValue }}
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
  }
};
</script>

<style>
.alert {
  background-color: red;
}
</style>
