<script>
export default {
    name: 'ProjectCard',
    props: {
        'project': {
            type: Object,
            required: true,
        },
        'isShow': {
            type: Boolean,
            required: false,
            default: false,
        }
    },
}
</script>
<template>
    <div class="card single-project">
        <div class="card-header text-center">
            <h3 class="card-title">{{ project.title }}</h3>
        </div>
        <div class="card-body d-flex flex-column justify-content-center align-items-center">
            <div class="card-image">
                <img v-if="project.image.startsWith('imgs/')" :src="'http://127.0.0.1:8000/storage/' + project.image"
                    :alt="project.title" class="img-fluid">
                <img v-else :src="project.image" alt="project.title" class="img-fluid">
            </div>
            <p class="card-text text-center">{{ project.content.substr(0, 100) }}...</p>
            <ul class="list-unstyled text-center mb-4">
                <li class="text-muted">Type: {{ project.type.name }}</li>
                <li class="text-muted">Author: {{ project.author }}</li>
                <li class="text-muted">
                    <span v-for=" technology in project.technologies">-{{ technology.name }} </span>
                </li>
            </ul>
            <router-link v-if="!isShow" :to="{ name: 'project', params: { slug: project.slug } }"
                class="btn btn-primary">Read
                More</router-link>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use '../styles/general.scss' as *;
</style>

