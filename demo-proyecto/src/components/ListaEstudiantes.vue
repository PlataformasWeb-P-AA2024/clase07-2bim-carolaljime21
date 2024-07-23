<template>
  <div>
    <h1>Lista de Estudiantes</h1>
    <center>
    <table class="mi-tabla">
      <tr>
        <th>Nombre</th>
        <th>Direccion</th>
        <th>Ciudad</th>
        <th>Tipo</th>
      </tr>
      <tr v-for="estudiante in estudiantes" :key="estudiante.id">
        <td>{{ estudiante.nombre }}</td>
        <td>{{ estudiante.direccion }}</td>
        <td>{{ estudiante.ciudad }}</td>
        <td>{{ estudiante.tipo }}</td>
      </tr>
    </table>
    </center>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      estudiantes: []
    };
  },
  created() {
    this.fetchEstudiantes();
  },
  methods: {
    async fetchEstudiantes() {
      try {
        const response = await axios.get('http://127.0.0.1:9000/api/edificios/');
        console.log(response.data.results);
        this.estudiantes = response.data.results;
      } catch (error) {
        console.error('Error obteniendo estudiantes:', error);
      }
    }
  }
};
</script>

<style scoped>
/* agregar ---- */
</style>
