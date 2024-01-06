<script setup>
import Header from './components/Header.vue'
</script>

<script>
export default {
    components: {
        Header,
    },
};
</script>

<template>
   <Header  title="Vue Laravel"/>
   <router-view></router-view>
</template>

<style scoped>

 
</style>
