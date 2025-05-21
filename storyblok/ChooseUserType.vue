<template>
    <div class="flex flex-row items-center justify-center gap-4">
        <button class="button choose-user-type-button" @click="goToHome">Homeowner</button>
        <button class="button choose-user-type-button" @click="goToHome">Landlord</button>
        <button class="button choose-user-type-button" @click="goToHome">Tenant</button>
    </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

defineProps({
    blok: Object,
});

const router = useRouter();

function goToHome() {
    router.push('/my/home');
}
</script>

<style scoped>
/* Add your styles here */
button {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    cursor: pointer;
    border-radius: 5px;
}
</style>