<script setup>
    import q from "./data/quizes.json"
    import { ref, watch } from "vue";
    import Card from "./components/Card.vue";

    const quizes = ref(q);
    const search = ref("");
    
    watch(search, () => {
        quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
    })

</script>

<template>
    <header>
        <nav>
            <div class="navbar bg-base-100">
                <div class="flex-1">
                    <a class="btn btn-ghost text-xl">Quiz App</a>
                </div>
                <div class="flex-none gap-2">
                    <div class="form-control">
                    <input v-model.trim="search" type="text" placeholder="Search" class="input input-bordered w-24 md:w-auto" />
                    </div>
                </div>
            </div>
        </nav>
    </header>
    <div class="options-container flex flex-wrap flex-row space-x-2 space-y-2">
        <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
        <!-- <div class="card w-1/4 bg-base-100 shadow-xl mt-4" v-for="quiz in quizes" :key="quiz.id">
            <figure><img :src="quiz.img" alt="placeholder" /></figure>
            <div class="card-body">
                <h2 class="card-title">{{ quiz.name }}</h2>
                <p>{{ quiz.questions.length }} questions</p>
            </div>
        </div> -->
    </div>
</template>

<style scoped>

</style>