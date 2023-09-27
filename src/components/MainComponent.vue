<script>
    import axios from 'axios';

    export default {
        name: "MainComponent",
        data() {
            return {
                projects: []
            }
        },
        methods: {},
        created(){
            axios.get('http://localhost:8000/api/projects')
                 .then(response => {
                    this.projects = response.data.results;
                })
                 .catch(error => {
                    console.error('Error:', error);
                });
        }
    }
</script>

<template>
    <main>
        <section>
            <div class="container mt-5">
                <div class="row text-center">
                    <div class="col" v-for="project in projects">
                        <h3 class="py-">{{ project.title }}</h3>
                        <img :src="project.img_link" alt="" class="w-100">
                        <p>{{ project.description }}</p>
                    </div>
                </div>
            </div>
        </section>
    </main>
</template>

<style lang="scss" scoped>
@use "../assets/scss/partials/variables.scss" as *;


</style>