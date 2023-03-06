<script >
import axios from 'axios';

export default {
    name: 'AppMain',
    data() {
        return {
            projects: [],
            apiUrl: 'http://127.0.0.1:8000/api/projects/',
        }
    },
    methods: {
        getProjects() {
            axios.get(this.apiUrl, {
                params: {

                }
            })
                .then((response) => {
                    this.projects = (response.data.results.data);

                })
                .catch(function (error) {
                    console.log(error);
                })
        }
    },
    created() {
        this.getProjects();
    },
}
</script>

<template >
    <section class="container">
        <div class="row">
            <div class="col-12">
                <h2>Projects</h2>
            </div>
        </div>
        <div class="row">
            <div class="col-3" v-for="project in projects">
                <div class="card">
                    <div class="card-header text-center">
                        <h3 class="card-title">{{ project.title }}</h3>
                    </div>
                    <div class="card-body d-flex flex-column justify-content-center align-items-center">
                        <div class="card-image">
                            <img v-if="project.image.startsWith('imgs/')"
                                :src="'http://127.0.0.1:8000/storage/' + project.image" :alt="project.title"
                                class="img-fluid">
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
                        <a href="#" class="btn btn-primary">Read more</a>
                    </div>
                </div>

            </div>
        </div>

    </section>
</template>

<style lang="scss"></style>