<template>
  <v-container class="d-flex justify-center align-center" style="height: 100vh;">
    <v-card class="pa-5" max-width="400">
      <v-card-title class="text-h5">Iniciar Sesión</v-card-title>
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
          <v-btn type="submit" color="primary" block>Ingresar</v-btn>
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