<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';
export default {
    name: "SingleProject",
    component: {
        ProjectCard,
    },
    data() {
        return {
            project: null,
            apiUrl: "http://127.0.0.1:8000/api/projects/",
        };
    },
    methods: {
        getProject() {
            axios.get(this.apiUrl + this.$route.params.slug, {
                params: {

                }
            })
                .then((response) => {
                    this.project = (response.data.results);
                })
                .catch(function (error) {
                    console.log(error);
                });
        }
    },
    created() {
        this.getProject();
    },
}
</script>

<template>
    <div>
        Home del singolo project {{ this.$route.params.slug }}
    </div>
    <div class="row">
        <ProjectCard :project="project" />
    </div>
</template>

<style lang="scss"></style>