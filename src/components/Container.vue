<template>
    <div id="container" class="container">
        <h2>Proyectos</h2>
        <img
            src="https://avatars.githubusercontent.com/u/22910053?v=4"
            alt="Avatar de CarlosSanz81"
            width="100"
            loading="lazy"
            class="image"
        />
        <hr />
        <loading v-if="load"></loading>
        <div id="cards" v-for="project in projects" :key="project.id">
            <card
                :name="project.name"
                :description="project.description"
                :author="project.owner.login"
                :url="project.html_url"
                :homepage="project.homepage"
            >
            </card>
        </div>
    </div>
</template>

<script>
import Card from "./Card.vue";
import Loading from "./Loading.vue";

export default {
    data() {
        return {
            projects: null,
            load: false,
        };
    },
    components: { Card, Loading },
    mounted() {
        this.getProjects();
    },
    methods: {
        async getProjects() {
            this.load = true;
            const res = await fetch(
                "https://api.github.com/users/CarlosSanz81/repos"
            );
            const data = await res.json();
            this.projects = data;
            this.load = false;
            console.log(data[1])
        },
    },
};
</script>

<style scoped>
.image {
    border-radius: 50%;
}
#cards {
    display: inline-flex;
    flex-wrap: wrap;
    justify-content: center;
}
.container {
    overflow: hidden;
    /* margin: 1rem;
    padding: 7px; */
    border: solid 1px #eee;
    box-shadow: 1px 1px 4px #333;
    text-align: center;
}
</style>