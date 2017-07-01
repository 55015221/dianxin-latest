

<template>
    <!--jumbotron-->
    <div class="banner">
        <img class="img-responsive center-block" src="/static/images/banner400.jpg" alt="">
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
    max-height: 360px;
    background: #3099E3;
}

</style>
