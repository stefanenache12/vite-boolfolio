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
            setTimeout(() => {
                axios.get('http://localhost:8000/api/projects')
                    .then(response => {

                        this.projects = response.data.results.data;
                       
                    })
                    .catch(error => {
                        console.error('Error:', error);
                    });
            }, 1500);
        }
    }
</script>

<template>
    <section v-if="projects.length > 0">
        <div class="container py-5 text-light">
            <div class="row text-center">
                <div class="col" v-for="project in projects">
                    <h3 class="py-3">{{ project.title }}</h3>
                    <div class="img-container w-100">
                        <router-link :to="{name: 'single-project', params: { id: project.id }}">
                        <img :src="project.img_link" alt="" class="w-100">
                    </router-link>
                    </div>
                    <p class="py-4">{{ project.description }}</p>
                    <h4 class="py-2">Technologies</h4>
                    <span class="badge text-bg-info mx-1" v-for="technology in project.technologies"> 
                        {{ technology.title }}
                    </span>
                    <h6 class="py-2">
                        Type: {{ project.type.title }}
                    </h6>
                </div>
            </div>
        </div>
    </section>
    <section v-else class="preloader-section">
        <div class="preloader">

        </div>

    </section>
</template>

<style lang="scss" scoped>
@use "../assets/scss/partials/variables.scss" as *;

.preloader-section {

    min-height: calc(100vh - 116px);
    display: flex;
    justify-content: center;
    align-items: center;
    .preloader {
    width: 200px;
    height: 200px;
    background-image: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200"><path fill="%23FF156D" stroke="%23FF156D" stroke-width="15" transform-origin="center" d="m148 84.7 13.8-8-10-17.3-13.8 8a50 50 0 0 0-27.4-15.9v-16h-20v16A50 50 0 0 0 63 67.4l-13.8-8-10 17.3 13.8 8a50 50 0 0 0 0 31.7l-13.8 8 10 17.3 13.8-8a50 50 0 0 0 27.5 15.9v16h20v-16a50 50 0 0 0 27.4-15.9l13.8 8 10-17.3-13.8-8a50 50 0 0 0 0-31.7Zm-47.5 50.8a35 35 0 1 1 0-70 35 35 0 0 1 0 70Z"><animateTransform type="rotate" attributeName="transform" calcMode="spline" dur="2" values="0;120" keyTimes="0;1" keySplines="0 0 1 1" repeatCount="indefinite"></animateTransform></path></svg>');
}

}

.img-container {
    position: relative;
    overflow: hidden;
    img {
        min-height: 290px;
        object-fit: cover;
        transition: transform 0.5s ease; 
        &:hover {
            transform: scale(1.2); 
        }
    }
}

</style>