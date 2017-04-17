<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="row row-items" v-for="(item ,index) in records" :style="(index%2 === 1)?'background: #e6e6e6;':''">
                <div class="container">
                    <div :class="(index%2 !== 1)?'col-sm-7 wow slideInLeft':'col-sm-7 col-sm-push-5 wow slideInRight'">
                        <h3>{{ item.title }}</h3>
                        <div class="details">
                            <span class="lead">{{ item.lead }}</span>
                            <p class="text-muted">{{ item.content }}</p>
                        </div>
                    </div>
                    <div :class="(index%2 !== 1)?'col-sm-5 wow slideInRight':'col-sm-5 col-sm-pull-7 wow slideInLeft'">
                        <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg" alt="400x250" :src="item.imageUrl" data-holder-rendered="true">
                    </div>
                </div>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'
import Jumbotron from '../../components/Jumbotron.vue'

export default {
    name: 'product',
    data () {
        return {
        }
    },
    components: {
        Jumbotron: Jumbotron
    },
    computed: {
        ...mapState({
            records: state => state.module.records
        })
    },
    created () {
        console.log("created product")
        this.$store.dispatch('getProduct',{ "method": "getProduct" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted product")
    },
    methods:{

    }
}
</script>

<style scoped>
.content .row {
    padding: 80px 0;
}
.content h3 {
    font-size: 36px;
}
.content .lead {
    font-size:18px;
    color: #3099E3;
    font-weight: 700;
}
.content .details p {
    margin-top: 8px;
}
</style>
