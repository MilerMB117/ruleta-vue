<template>
  <div>
    <h2>Apuesta</h2>
    <form @submit.prevent="apostar">
      <div>
        <label for="monto">Monto: </label>
        <input type="number" v-model="monto" required>
      </div>
      <div>
        <label for="apuesta">Apuesta: </label>
        <input type="text" v-model="apuesta" required>
      </div>
      <button type="submit">Apostar</button>
    </form>
    <div v-if="resultadoApuesta">
      <p>Resultado de la apuesta: {{ resultadoApuesta }}</p>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'ApuestaComponent',
  data() {
    return {
      monto: 0,
      apuesta: '',
      resultadoApuesta: null
    };
  },
  props: {
    resultadoRuleta: {
      type: Object,
      default: null
    }
  },
  methods: {
    async apostar() {
      try {
        const response = await axios.post(`https://localhost:5001/ruleta/premio`, {
          montoApostado: this.monto,
          apuesta: this.apuesta,
          resultadoRuleta: this.resultadoRuleta
        });
        this.resultadoApuesta = response.data;
      } catch (error) {
        console.error('Error al apostar:', error);
      }
    }
  }
};
</script>
