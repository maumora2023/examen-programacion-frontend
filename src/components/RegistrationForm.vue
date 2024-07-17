<template>
  <div class="card">
    <div class="card-body">
      <h3>Formulario de registro</h3>
      <form @submit.prevent="register">
        <div class="form-group">
          <label for="name">Nombre</label>
          <input id="name" v-model="name" type="text" class="form-control" required>
        </div>
        <div class="form-group">
          <label for="email">Correo</label>
          <input id="email" v-model="email" type="email" class="form-control" required>
        </div>
        <div class="form-group">
          <label for="password">Contraseña</label>
          <input id="password" v-model="password" type="password" class="form-control" required>
        </div>
        <div class="form-group">
          <label for="confirmPassword">Repetir Contraseña</label>
          <input id="confirmPassword" v-model="confirmPassword" type="password" class="form-control" required>
        </div>
        <button type="submit" class="btn btn-primary">Enviar</button>

        <!-- Mensaje de error debajo del botón -->
        <div v-if="errorMessage" class="error-message mt-3">
          {{ errorMessage }}
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: '',
      email: '',
      password: '',
      confirmPassword: '',
      errorMessage: ''
    };
  },
  methods: {
    register() {
      this.errorMessage = '';

      // Validación de campos
      if (this.password !== this.confirmPassword) {
        this.errorMessage = 'Las contraseñas no coinciden.';
        return;
      }

      // Aquí puedes agregar más validaciones y lógica para enviar los datos
      alert('Formulario enviado con éxito.');
    }
  }
}
</script>

<style scoped>
.error-message {
  color: red;
  margin-top: 10px;
}

.mt-3 {
  margin-top: 1rem;
}
</style>
