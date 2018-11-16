<template>


      <div class="card-content" id="content">

        <form @submit.prevent="$emit('show-swag', totalSwag)">

          <div class="field">
              <label class="label"> Edad </label>
            <div class="control">
              <input type="number" class="input"  v-model.number="age" min=0 placeholder=18 :class="[ age < 1 ? 'is-danger' : 'is-success' ]">
            </div>
          </div>

          <div class="field">
            <label class="label"> Sexo </label>
            <div class="is-grouped">
              <div class="control">
                <label class="radio">
                  <input type="radio" name="gender" value="Macho" v-model='sex'> Macho
                </label>
                <label class="radio">
                  <input type="radio" name="gender" value="Hembra" v-model='sex'> Hembra
                </label>
              </div>
            </div>
          </div>

          <div class="field">
            <label class="label"> Estatura </label>
            <div class="control">
              <input type="number" min="0" step="0.01" v-model.number="height" class="input" :class="[ height < 0.1 ? 'is-danger' : 'is-success' ]">
            </div>
          </div>

          <div class="field">
            <label class="label"> Peso </label>
            <div class="control">
              <input type="number" min="0" step="0.1" v-model.number="weight" class="input" :class="[ weight < 0.1 ? 'is-danger' : 'is-success' ]">
            </div>
          </div>

          <div class="field"  v-if="sex=='Macho'">
            <label class="label"> Talla de zapato </label>
              <div class="control">
                <input type="number" min="0"  v-model.number="footSize" class="input" :class="[ footSize < 1 ? 'is-danger' : 'is-success' ]">
              </div>
          </div>

          <div class="field" v-else> 
            <label class="label"> Talla de sujetador </label>
              <div class="control">
                <input type="number" min="0" step="5" v-model.number="braSize" class="input" :class="[ braSize < 1 ? 'is-danger' : 'is-success' ]">
              </div>
          </div>
          
          <div class="field">
            <label class="label"> Nivel de estudios </label>
              <div class="select">
                <select v-model="studies">
                  <option>Ninguno</option>
                  <option>Primaria</option>
                  <option>Secundaria</option>
                  <option>Medio</option>
                  <option>Superior</option>
                </select>
              </div>
          </div>


          <div class="field">
            <input type="submit" value="Calcular" class="button">
          </div>

        </form>

      </div>


</template>




<script>
export default {

  data() {
    return {
      age: 18,
      height: 1.65,
      weight: 60,
      sex: "Macho", 
      footSize: 40,
      braSize: 80,
      studies: "Ninguno",
    };
  },

  computed: {
      totalSwag() {
        return this.age +  this.height*20 + this.weight*30 + (this.sex=='Macho' ? this.footSize*1000 : this.braSize*500);
      }
  },



}

</script>


<style>
    
</style>