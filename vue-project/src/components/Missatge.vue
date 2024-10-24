<template>
    <div class="missatge-form">
      <form @submit.prevent="enviarMissatge">
        <input v-model="text" type="text" placeholder="Escriu el teu missatge" />
        <button type="submit">Enviar</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import { defineProps, defineEmits } from 'vue';
  
  // DProps
  const props = defineProps({
    autor: String
  });


  const emit = defineEmits(['enviar-missatge']);
  
  // Variable reactiva per emmagatzemar el text del missatge
  const text = ref('');
  
  // Funció per enviar el missatge al component pare
  function enviarMissatge() {
    if (text.value.trim() !== '') {
      // Emetre el missatge amb l'autor i el text
      emit('enviar-missatge', {
        autor: props.autor,
        text: text.value
      });
      // Netejar el camp un cop enviat el missatge
      text.value = '';
    }
  }
  </script>
  
  <style scoped>
 
  </style>
  