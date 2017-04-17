

<template>
    <!--jumbotron-->
    <div class="banner">
        <img class="img-responsive" src="/static/images/解决方案_02.png" alt="First slide">
    </div>
</template>


<script>
export default {
    name: 'jumbotron',
    data () {
        return {

        }
    },
    components: {
    },
    computed: {

    },
    created () {
        console.log("created jumbotron")
    },
    mounted () {
        console.log("mounted jumbotron")
    },
    methods:{

    }
}
</script>

<style scoped>
.banner {
    background: #3099E3;
}

</style>
