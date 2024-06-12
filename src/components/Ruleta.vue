<template>
    <div>
      <h2>Ruleta</h2>
      <button @click="generarResultado">Girar Ruleta</button>
      <div v-if="resultado">
        <p>Resultado: {{ resultado.numero }} - {{ resultado.color }}</p>
        <p>{{ resultado.numero % 2 === 0 ? 'Par' : 'Impar' }}</p>
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  
  export default {
    name: 'RuletaComponent', // Renamed the component to a multi-word name
    data() {
      return {
        resultado: null
      };
    },
    methods: {
      async generarResultado() {
        const response = await axios.get('https://localhost:5001/api/ruleta/generar');
        this.resultado = response.data;
      }
    }
  };
  </script>
  