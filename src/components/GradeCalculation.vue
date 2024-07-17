<template>
    <div class="container mt-4">
      <form @submit.prevent="submitForm">
        <div class="form-group">
          <label for="nota1">Nota 1 </label>
          <input type="number" id="nota1" v-model.number="nota1" min="10" max="70" class="form-control" required>
        </div>
        <div class="form-group">
          <label for="nota2">Nota 2 </label>
          <input type="number" id="nota2" v-model.number="nota2" min="10" max="70" class="form-control" required>
        </div>
        <div class="form-group">
          <label for="nota3">Nota 3 </label>
          <input type="number" id="nota3" v-model.number="nota3" min="10" max="70" class="form-control" required>
        </div>
        <div class="form-group">
          <label for="asistencia">Asistencia (%):</label>
          <input type="number" id="asistencia" v-model.number="asistencia" min="0" max="100" class="form-control" required>
        </div>
        <button type="submit" class="btn btn-primary">Calcular</button>
        <div>
          <p v-if="promedio !== ''" class="textoResultado">El promedio es: {{ promedio.toFixed(2) }}</p>
          <p v-if="resultado !== ''" class="textoResultado" :class="{'text-success': resultado === '¡Aprobado!', 'text-danger': resultado === 'Reprobado'}">{{ resultado }}</p>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        nota1: null,
        nota2: null,
        nota3: null,
        asistencia: null,
        promedio: '',
        resultado: ''
      };
    },
    methods: {
      submitForm() {
        this.calcularResultado();
      },
      calcularResultado() {
        if (this.nota1 !== null && this.nota2 !== null && this.nota3 !== null && this.asistencia !== null) {
          this.promedio = (this.nota1 * 0.35) + (this.nota2 * 0.35) + (this.nota3 * 0.30);
          this.resultado = (this.promedio >= 40 && this.asistencia >= 80) ? '¡Aprobado!' : 'Reprobado';
        } else {
          this.promedio = '';
          this.resultado = 'Por favor ingresa todas las notas y la asistencia.';
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .form-control {
    margin-bottom: 15px;
  }
  
  .btn-primary {
    background-color: #007bff;
    border-color: #007bff;
  }
  
  .btn-primary:hover {
    background-color: #0056b3;
    border-color: #004085;
  }
  
  .textoResultado {
    font-weight: bold;
    margin-top: 10px;
  }
  
  .text-success {
    color: #28a745;
  }
  
  .text-danger {
    color: #dc3545;
  }
  
  .container {
    max-width: 600px;
    margin: auto;
  }
  </style>
  