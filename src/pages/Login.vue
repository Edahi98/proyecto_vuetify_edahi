<template>
  <v-container class="d-flex justify-center align-center" style="height: 100vh;">
    <v-card class="pa-8" max-width="500">
      <v-card-title class="text-h4">Iniciar Sesión</v-card-title>
      <v-card-text>
        <v-form @submit.prevent="handleLogin" ref="formRef">
          <v-text-field
            v-model="password"
            label="Contrseña"
            type="password"
            required
          ></v-text-field>
          <v-text-field
            v-model="userName"
            label="Nombre de usuario"
            type="password"
            required
          ></v-text-field>
          <v-alert
          type="error"
          variant="tonal"
          v-if="errorMessage"
          class="mt-4 mb-6"
          border="start">
            {{ errorMessage }}
          </v-alert>
          <v-btn type="submit" color="primary" block class="mt-4">Ingresar</v-btn>
        </v-form>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import axiosInstance from '@/config/axios';

const userName = ref('');
const password = ref('');
const errorMessage = ref('');
const router = useRouter();

const loading = ref(false);
const showPassword = ref(false);

const handleLogin = () => {
  try {
    if(!userName.value || !password.value){
      errorMessage.value = "Rellena todos los datos";
      return
    }
  } catch (e) {
    errorMessage.value = "";
  }
};
</script>