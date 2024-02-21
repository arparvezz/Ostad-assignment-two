<script setup>
import { ref } from 'vue';
let url = 'https://animechan.xyz/api/random';
let outputObject = ref({})
function getData() {
    fetch(url)
        .then(rawData => rawData.json())
        .then(data => outputObject.value = data)
        // .then(data => document.querySelector('.output_data').innerHTML = JSON.stringify(data))
        .catch(error => console.log(error))
}
</script>

<template>
    <div class="container mx-auto">
        <div class="sm:w-full md:w-1/3 lg:w-1/3 mx-auto m-5 p-3 rounded border bg-slate-50">
            <h2 class="text-2xl">Fetch Data from api</h2>
            <button @click="getData()" class="px-2 py-1 rounded outline-none border-none bg-purple-200 hover:bg-purple-300 cursor-pointer">Get Quote</button>
            <div class="my-1 p-2 bg-slate-200 rounded">
                <div class="output_data">
                    
                    <span class="text-blue-500">ID: {{ outputObject.id }}</span><p>Quote: {{ outputObject.quote }}</p>
                    - <span> {{ outputObject.character }}</span>
                    <p>Anime: {{ outputObject.anime }}</p>
                    <!-- <p>Quote: {{ outputObject.value.quote || '' }}</p> -->
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped></style>
