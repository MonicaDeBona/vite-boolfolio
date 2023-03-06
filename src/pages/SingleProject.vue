<script>
import axios from 'axios';
import ProjectCard from '../components/ProjectCard.vue';
export default {
    name: "SingleProject",
    components: {
        ProjectCard,
    },
    data() {
        return {
            project: [],
            apiUrl: "http://127.0.0.1:8000/api/projects/",
        };
    },
    methods: {
        getProject() {
            axios.get(this.apiUrl + this.$route.params.slug, {
                params: {
                    'api_token': 'S2AtUREfT9fPQYfTq4sCKq35O2MJ9vtJOQUwBhx4LU2cEAB8CJo2H84tL7bWnsTxObV6P0QQkLJqNkIU',
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
    <div class="row">
        <ProjectCard :project="project" :isShow="true" />
    </div>
</template>

<style lang="scss"></style>