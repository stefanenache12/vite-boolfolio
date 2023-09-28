<script>
    import axios from 'axios';

    export default {
        name: "HomePage",
        data() {
            return {
                projects: [],
               
            }
        },
        methods: {},
        created(){
            axios.get('http://localhost:8000/api/projects')
                 .then(response => {
                    this.projects = response.data.results.data;
                    
                })
                 .catch(error => {
                    console.error('Error:', error);
                });
        }
    }
</script>

<template>
    <section class="w-100">
        <div class="hero">

        </div>
        <div class="container text-light">
            <div class="row text-center">
                <div class="col">
                    <h1 class="py-4">
                        Welcome on My Portofolio
                    </h1>
                    <button class="btn btn-dark">
                        <router-link :to="{name: 'projects'}"> View My Projects </router-link>
                    </button>
                </div>
            </div>
        </div>
    </section>
</template>

<style lang="scss" scoped>
@use "../assets/scss/partials/variables.scss" as *;

section {
    
    min-height: calc(100vh - 116px);

    .hero {
        width: 100%;
        height: 350px;
        background-position: center;
        object-fit: fill;
        background-image: url(https://images.pexels.com/photos/633409/pexels-photo-633409.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1);
        
    }

    a {
        color: white;
        text-decoration: none;
    }
}
</style>