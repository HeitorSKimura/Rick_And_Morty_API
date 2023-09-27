<script setup>

import ModalCharacter from './ModalCharacter.vue';

const character = defineProps(["id","name","image"])


</script>

<template>
    <!-- Criação de cards -->
    <div class="col-4">
        <div class="card mb-3 border border-3 border-dark bg-primary-subtle">
            <img class="card-img-top" :src="character.image">
            <div class="card-body">
                <h5 class="card-text-center">{{character.name}}</h5>
                <!-- Chamada para o componente ModalCharacter -->
                <ModalCharacter 
                :id=character.id
                />
            </div>
            
        </div>
    </div>
</template>

<style>

</style>