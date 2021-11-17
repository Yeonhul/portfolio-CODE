<template>
    <div :class="['app_div',`app_back${$store.state.app_back}`]">
        <He />
        <router-view></router-view>
    </div>
</template>

<script>
export default {
    methods : {
        load() {
            var route = this.$route.name
            this.$store.commit('background', route);
        }
    },
    mounted() {
        window.addEventListener('load', this.load)
    },
    beforeDestory() {
        window.removeEventListener('resize', this.load);
    },
    watch:{ 
        '$route' (to, from) {
            this.$store.commit('background', to.name);
        }
    },
}
</script>

<style lang="scss">
@import '@/scss/header.scss';
@import '@/scss/profile.scss';
@import '@/scss/project.scss';
@import '@/scss/blog.scss';
</style>
