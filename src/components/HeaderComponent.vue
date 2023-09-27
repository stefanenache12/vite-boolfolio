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
                            Home
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
        background-color: black;
        color: white;
    }
</style>