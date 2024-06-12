<template>
  <div>
    <h2>Saldo</h2>
    <form @submit.prevent="guardarSaldo">
      <div>
        <label for="nombre">Nombre: </label>
        <input type="text" v-model="nombre" required>
      </div>
      <div>
        <label for="monto">Monto: </label>
        <input type="number" v-model="monto" required>
      </div>
      <button type="submit">Guardar Saldo</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
import https from 'https'; // Importa el módulo https

export default {
  name: 'SaldoComponent', // Renombrado el componente a "SaldoComponent"
  data() {
    return {
      nombre: '',
      monto: 0
    };
  },
  methods: {
    async guardarSaldo() {
      try {
        const agent = new https.Agent({ rejectUnauthorized: false }); // Crea un nuevo agente https con la opción rejectUnauthorized en false
        await axios.post('https://localhost:5001/api/usuario/guardar', {
          nombre: this.nombre,
          monto: this.monto
        }, { httpsAgent: agent }); // Usa el agente https en la solicitud
      } catch (error) {
        console.error('Error al guardar el saldo:', error);
      }
    }
  }
};
</script>
