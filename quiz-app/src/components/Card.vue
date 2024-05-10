<script setup>

    const {quiz} = defineProps(['quiz'])
</script>

<template>
    <div class="card w-1/4 bg-base-100 shadow-xl mt-4">
            <figure><img :src="quiz.img" alt="placeholder" /></figure>
            <div class="card-body">
                <h2 class="card-title">{{ quiz.name }}</h2>
                <p>{{ quiz.questions.length }} questions</p>
            </div>
        </div>
</template>