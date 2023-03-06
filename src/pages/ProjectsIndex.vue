<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';

export default {
    name: 'ProjectsIndex',
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

<template>
    <div class="row">
        <div class="col-12">
            Projects
        </div>
    </div>
    <div class="row">
        <ProjectCard v-for="project in projects" :project="project" class="col-4" />
    </div>
</template>

<style lang="scss"></style>
