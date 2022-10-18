<script setup>
import { ref } from 'vue';
const data = ref(null)
const title = ref(null)
const tanggal = ref(null)
const statusnya = ref(null)
const error = ref(null)
function showTan() {
    fetch('http://laravel-api.test/api/posts')
        .then((res) => res.json())
        .then((json) => (data.value = json))
        .catch((err) => (error.value = err))
}

function inputTan() {
    const requestOptions = {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: {
            title: title,
            tanggal: tanggal,
            status: statusnya,
        }
    };
    // console.log(title);
    // console.log(tanggal);
    // console.log(statusnya);
    fetch("https://laravel-api.test/api/posts", requestOptions)
        .then(response => response.json())
        .catch((err) => (error.value = err))
}
showTan();

</script>
    
<template>
    <div class="mx-auto py-4">
        <h2 class="text-lg font-extrabold underline underline-offset-8 text-[#525252] my-4">
            To do list :
            {{response}}
        </h2>
        <div class="flex space-x-2">
            <input v-model="title"
                class="text-[#525252] font-bold bg-[#f6ffff] border-4  border-[#525252] rounded-lg border-shadow1"
                type="text" name="" id="" placeholder="Tittle">
            <input v-model="tanggal"
                class="text-[#525252] font-bold bg-[#f6ffff] border-4 border-[#525252] rounded-lg border-shadow1"
                type="date" name="" id="">
            <input v-model="statusnya" placeholder="Status"
                class="text-[#525252] font-bold bg-[#f6ffff] w-32 border-4 border-[#525252] rounded-lg border-shadow1"
                type="text" name="" id="">
            <div class="border-shadow1 bg-[#525252] rounded-lg active:bg-[#fff5d9] cursor-pointer">
                <button @click="inputTan"
                    class="text-[#525252] font-bold bg-[#f6ffff] px-2 border-4 border-[#525252] rounded-lg active:translate-x-[4px] active:translate-y-[3px]">
                    Add </button>
            </div>
        </div>
        <div class="bg-[#f6ffff] border-4 border-[#525252] rounded-lg p-4 my-4">
            <h3 class="text-lg font-extrabold border-b-4 border-[#525252] border-dashed text-[#525252]">
                Your list :
            </h3>
            <div v-for="item in data">
                <div class="bg-white border-4 flex space-x-3 border-[#525252] rounded-lg p-2 my-3">
                    <div class="border-r-4 border-[#525252] border-dashed p-2 w-4/5 overflow-auto">
                        <p class="text-base font-extrabold text-[#525252]">
                            {{item.title}}
                        </p>
                    </div>
                    <div class="border-r-4 border-[#525252] border-dashed p-2">
                        <p class="text-base font-extrabold text-[#525252]">
                            {{item.tanggal}}
                        </p>
                    </div>
                    <div class="border-r-4 border-[#525252] border-dashed p-2">
                        <p class="text-base font-extrabold text-green-600">
                            {{item.status}}
                        </p>
                    </div>
                    <div class=" p-2">
                        <div class="flex space-x-1">
                            <i class="fa-solid fa-square-check text-3xl font-extrabold text-[#525252]"></i>
                            <i class="fa-solid fa-square-xmark text-3xl font-extrabold text-[#525252]"></i>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

