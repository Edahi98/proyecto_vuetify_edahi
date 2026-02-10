<template>
  <v-container class="d-flex justify-center align-center" style="height: 100vh;">
    <v-card class="pa-8" max-width="500">
      <v-card-title class="text-h4">Iniciar Sesión</v-card-title>
      <v-card-text>
        <v-form @submit.prevent="handleLogin" ref="formRef">
          <v-text-field
            v-model="email"
            label="Correo Electrónico"
            type="email"
            :rules="emailRules"
            required
          ></v-text-field>
          <v-text-field
            v-model="password"
            label="Contraseña"
            type="password"
            required
          ></v-text-field>
          <v-alert
          type="error"
          variant="tonal"
          class="mt-4 mb-6"
          border="start">
            errorMessage
          </v-alert>
          <v-btn type="submit" color="primary" block class="mt-4">Ingresar</v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup>
import { ref } from 'vue';

const email = ref('');
const password = ref('');
const formRef = ref(null);

const emailRules = [
  (v) => !!v || 'El correo electrónico es obligatorio.',
  (v) => /.+@.+\..+/.test(v) || 'Debe ser un correo electrónico válido.',
];

const handleLogin = () => {
  if (formRef.value.validate()) {
    console.log('Correo:', email.value);
    console.log('Contraseña:', password.value);
    // Aquí puedes agregar la lógica para autenticar al usuario
  } else {
    alert('Por favor, corrige los errores en el formulario.');
  }
};
</script>