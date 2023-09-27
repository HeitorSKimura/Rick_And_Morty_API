<script setup>
import { onMounted, reactive, ref} from 'vue';
import ListCharacters from '../components/ListCharacters.vue';

let characters = reactive(ref());

// Chamada para a API trazendo o resultado em json para a variavel characters
onMounted(() => {
  fetch("https://rickandmortyapi.com/api/character/?limit=20&offset=0")
  .then(response => response.json())
  .then(response => {
    characters.value = response.results;
    console.log(response);
  })
})

</script>

<template>
  <main>
    <!-- Criação de cards dentro de uma container -->
    <div class="container">
      <div class="row mt-4">
        <div class="card row-center bg-dark-subtle">
          <div class="card-body row row-cols-md-5">
            <!-- Chamada para o componente ListCharacters onde retorna uma lista para cada personagem chamado na API -->
            <ListCharacters
            v-for="character in characters"
            :id="character.id"
            :name="character.name"
            :image="character.image"
            :status="character.status"
            :species="character.species"
            :gender="character.gender"
            />
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
