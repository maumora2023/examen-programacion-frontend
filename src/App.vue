<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link" @click="currentTab = 'grade'" :class="{ active: currentTab === 'grade' }">Cálculo de calificaciones</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" @click="currentTab = 'register'" :class="{ active: currentTab === 'register' }">Formulario de Registro</a>
          </li>
        </ul>
        <form class="form-inline ml-auto">
          <!-- Aquí puedes agregar elementos de formulario si es necesario -->
        </form>
      </div>
    </nav>

    <div class="container mt-4">
      <GradeCalculation v-if="currentTab === 'grade'" />
      <RegistrationForm v-if="currentTab === 'register'" />
    </div>
  </div>
</template>

<script>
import GradeCalculation from './components/GradeCalculation.vue';
import RegistrationForm from './components/RegistrationForm.vue';

export default {
  name: 'App',
  components: {
    GradeCalculation,
    RegistrationForm
  },
  data() {
    return {
      currentTab: 'grade' // La pestaña inicial seleccionada
    };
  }
}
</script>

<style>
body {
  font-family: Arial, sans-serif;
}

.navbar {
  margin-bottom: 20px;
}

.nav-link.active {
  font-weight: bold;
  color: #007bff; /* Ajusta el color según tus necesidades */
}
</style>
