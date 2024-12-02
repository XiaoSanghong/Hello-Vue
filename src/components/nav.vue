<template>
    <div>
        <nav>
            <router-link v-for="(navDoc,ind) in navbarList" :key="ind" :to="navDoc.path">{{navDoc.title}}</router-link>
            <!-- <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link> |
            <router-link to="/contact">Contact</router-link> |
            <router-link to="/product">Product</router-link> -->
        </nav>
    </div>
</template>

<script>
    export default {
        name:"NavView",
        data() {
            return {
                navbarList: [
                    {title:"Home |", path:"/"},
                    {title:"About | ", path:"/About"},
                    {title:"Contact |", path:"/Contact"},
                    {title:"Product ", path:"/Product"},
                ]
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>