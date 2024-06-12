<template>
  <div id="app">
    <h1>Juego de la Ruleta</h1>
    <Ruleta ref="ruleta"></Ruleta>
    <Apuesta :resultadoRuleta="resultadoRuleta"></Apuesta>
    <Saldo></Saldo>
  </div>
</template>

<script>
import Ruleta from './components/Ruleta.vue';
import Apuesta from './components/ApuestaComponent.vue';
import Saldo from './components/Saldo.vue';

export default {
  name: 'App',
  components: {
    Ruleta,
    Apuesta,
    Saldo
  },
  data() {
    return {
      resultadoRuleta: null
    };
  },
  methods: {
    
  }
};
</script>
