<template>
    <!--carousel-->
    <div style="background: #3099E3;margin: 0;">
        <div id="myCarousel" class="carousel slide" data-ride="carousel">
            <!-- Indicators -->
            <ol class="carousel-indicators">
                <template v-for="(items, index) in banner">
                    <li data-target="#myCarousel" v-bind:data-slide-to="index" v-bind:class="(index === 0 ? 'active' : '')"></li>
                </template>
            </ol>
            <div class="carousel-inner" role="listbox">
                <template v-for="(items, index) in banner">
                    <div v-bind:class="'item' + (index === 0 ? ' active' : '')">
                        <img class="first-slide" v-bind:src="items.imageUrl" v-bind:alt="items.title">
                    </div>
                </template>
            </div>
        </div>
    </div>
</template>


<script>
export default {
    name: 'carousel',
    data () {
        return {
            banner: [
                { "imageUrl": "/static/images/banner_01.png", "title": "", linkUrl: "" },
                { "imageUrl": "/static/images/banner_02.png", "title": "", linkUrl: "" },
                { "imageUrl": "/static/images/banner_03.png", "title": "", linkUrl: "" },
            ]
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
