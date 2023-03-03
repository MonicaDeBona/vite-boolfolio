<script>
export default {
    name: 'ProjectCard',
    props: {
        title: String,
        image: String,
        content: String,
        type: Object,
        author: String,
        technologies: Array,
    },
}
</script>
<template>
    <div class="card single-project">
        <div class="card-header text-center">
            <h3 class="card-title">{{ title }}</h3>
        </div>
        <div class="card-body d-flex flex-column justify-content-center align-items-center">
            <div class="card-image">
                <img v-if="image.startsWith('imgs/')" :src="'http://127.0.0.1:8000/storage/' + image" :alt="title">
                <img v-else :src="image" alt="title">
            </div>
            <p class="card-text text-center">{{ content }}</p>
            <ul class="list-unstyled text-center mb-4">
                <li class="text-muted">Type: {{ type.name }}</li>
                <li class="text-muted">Author: {{ author }}</li>
                <li class="text-muted">
                    <span v-for=" technology in technologies">-{{ technology.name }} </span>
                </li>
            </ul>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
</style>

