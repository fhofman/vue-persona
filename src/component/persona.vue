<template>
<div>
  <template v-if="persona">
    <h1 v-text="datosPersona.nombre"></h1>
    <h2 v-text="datosPersona.correoe"></h2>
    <img :src="datosPersona.foto">
  </template>
</div>
</template>

<script>
import axios from 'axios';
export default {
  mounted(){
    axios.get("https://randomuser.me/api/")
    .then((respuesta) => {
      this.persona = respuesta.data.results[0];
    })
  },
  data(){
    return {
      persona:null,
    }
  },
  computed:{
    datosPersona(){
      return {
        nombre: `${this.persona.name.first} ${this.persona.name.last}`,
        correoe: this.persona.email,
        foto: this.persona.picture.large,
      }
    }
  }
}
</script>

<style>
</style>
