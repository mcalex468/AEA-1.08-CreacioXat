    <template>
        <div class="chat-container">
        <h2>Xat</h2>
    
        <!-- Llista de missatges -->
        <ul>
            <li v-for="(missatge, index) in missatges" :key="index">
           {{ missatge.autor }} : {{ missatge.text }}
            </li>
        </ul>
    
        <!-- Component fill Missatge.vue  -->
        <Missatge @enviar-missatge="afegirMissatge" :autor="autor" />
        </div>
    </template>
    
    <script setup>
    import { ref } from 'vue';
    import Missatge from './Missatge.vue';
    
    // Crear una variable reactiva per gestionar la llista de missatges
    const missatges = ref([]);
    
    // Definir l'autor del missatge
    const autor = 'Usuari1';
    
    // Funció per afegir un missatge a la llista
    function afegirMissatge(nouMissatge) { 
        missatges.value.push(nouMissatge);
    }
    </script>
    
    <style scoped>
   
    </style>
    