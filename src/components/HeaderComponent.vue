<script>
export default {
    name: "HeaderComponent",
    data() {
        return {

        }
    },
    methods: {

    }
}
</script>

<template>
    <header>
        <nav>
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-6">
                        <div class="logo">
                            <h1>
                                MyPortofolio
                            </h1>
                        </div>
                    </div>
                    <div class="col-6 text-end">
                        <div class="nav-links">
                            <ul>
                                <li>
                                    <router-link :to="{name: 'home'}"> Home </router-link>
                                </li>
                                <li>
                                    <router-link :to="{name: 'projects'}"> Projects </router-link>
                                </li>
                            </ul>
                        </div>
                    </div>
                </div>
            </div>
        </nav>
    </header>
</template>

<style lang="scss" scoped>
    nav {
        padding: 30px 0;
        background-color: rgba(0, 0, 0, 0.451);
        color: white;

        ul {
            list-style: none;
            display: flex;
            justify-content: end;

            li {
                padding-left: 15px;

                a {
                    text-decoration: none;
                    color: white;
                    font-size: 1.2rem;
                    transition: all 0.3s ease;

                    &:hover{
                        color: orange;
                    }
                }
            }
        }
    }
</style>