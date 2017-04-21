<template>
    <!--carousel-->
    <div style="background: #3099E3;margin: 0;">
        <div id="myCarousel" class="carousel slide" data-ride="carousel">
            <!-- Indicators -->
            <ol class="carousel-indicators">
                <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
                <li data-target="#myCarousel" data-slide-to="1" class=""></li>
            </ol>
            <div class="carousel-inner" role="listbox">
                <div class="item active">
                    <img class="first-slide" src="/static/images/banner.png" alt="">
                </div>
                <div class="item">
                    <img class="second-slide" src="/static/images/banner.png" alt="">
                </div>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name: 'carousel',
    data () {
        return {

        }
    },
    components: {
    },
    computed: {

    },
    created () {
        console.log("created carousel")
    },
    mounted () {
        console.log("mounted carousel")
    },
    methods:{

    }
}
</script>

<style scoped>


</style>
