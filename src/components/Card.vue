<template>
    <div id="card" class="card">
        <h4>{{ name }}</h4>
        <p>
            {{ description }}
        </p>
        <p>
            <strong>{{ author }}</strong>
        </p>
        <button-url :url="url" color="danger" title="Git Hub" />
        <button-url :url="homepage" color="success" v-if="homepage != null" title="HomePage"/>
    </div>
</template>

<script>
import ButtonUrl from "./ButtonUrl.vue";
export default {
    components: { ButtonUrl },
    props: {
        name: String,
        description: String,
        author: String,
        color: String,
        url: String,
        homepage: String,
        title: String,
    },
};
</script>
<style scoped>
.card {
    width: 250px;
    margin: 1rem;
    padding: 7px;
    border: solid 1px #eee;
    box-shadow: 1px 1px 4px #333;
    text-align: center;
}
</style>