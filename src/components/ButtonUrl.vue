<template>
    <div id="buttonurl">
        <a :href="url" :class="setColor" target="_blank">{{ title }}</a>
    </div>
</template>

<script>
export default {
    props: {
        color: String,
        url: String,
        title: String,
    },
    computed: {
        setColor() {
            return `btn btn-${this.color} m-1`;
        },
    },
};
</script>

<style>
</style>