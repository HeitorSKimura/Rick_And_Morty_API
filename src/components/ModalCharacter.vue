<script setup>


import { onMounted, ref} from 'vue';

const open = ref(false)
const char = defineProps(["id"])
const info = ref(null);

// Requisição para a API na qual aguarda uma chamada e retorna as informaçoes em json para a variavel info
onMounted(async() => {
    const response = await fetch("https://rickandmortyapi.com/api/character/"+char.id);
    const data = await response.json();
    info.value = await data.result;
    await console.log(response);
})




</script>

<template>
    <!-- Botão dentro de um card(no componente ListCharacters) na qual chama um modal -->
    <button type="button" @click="open" class="btn btn-dark btn-sm" data-bs-toggle="modal" :data-bs-target="`#charModal${char.id}`">Info</button>

    <!-- Modal com id para cada char.id -->
    <div class="modal fade" :id="`#charModal${char.id}`" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="card">
                    <div class="card-body">
                        <p>{{char.id}}</p>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>