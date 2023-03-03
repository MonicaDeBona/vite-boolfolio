<script >
import axios from 'axios';

import ProjectCard from './ProjectCard.vue';
export default {
    name: 'AppMain',
    components: {
        ProjectCard,
    },
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
                Projects
            </div>
        </div>

        <div class="projects">
            <ProjectCard v-for="project in projects" :title="project.title" :image="project.image"
                :content="project.content" :type="project.type" :author="project.author"
                :technologies="project.technologies" />
        </div>
    </section>
</template>

<style lang="scss"></style>