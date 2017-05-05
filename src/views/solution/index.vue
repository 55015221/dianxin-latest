<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="container">
                <div class="row">
                    <ul class="nav nav-tabs" role="tablist">
                        <template v-for="(items, index) in records">
                            <li role="presentation" v-bind:class="index === 0?'active':''">
                                <a v-bind:href="'#panel-'+index" role="tab" data-toggle="tab" aria-controls="profile" aria-expanded="true">{{ items.title }}</a>
                            </li>
                        </template>
                    </ul>
                    <div class="tab-content">
                        <template v-for="(items, index) in records">
                            <div role="tabpanel" class="tab-pane fade active in" v-bind:id="'panel-'+ index" aria-labelledby="profile-tab">
                                <div class="col-sm-6">
                                    <div class="panel">
                                        <div class="panel-heading">
                                            <h3 class="panel-title">{{ items.content.subheading }}</h3>
                                            <small></small>
                                        </div>
                                        <div class="panel-body">
                                            <template v-if="items.content.body instanceof Array">
                                                <ul>
                                                    <li v-for="(val, idx) in items.content.body">{{ val}}</li>
                                                </ul>
                                            </template>
                                            <template v-else>
                                                {{ items.content.body }}
                                            </template>
                                        </div>
                                    </div>
                                </div>
                                <div class="col-sm-6">
                                    <img class="img-responsive center-block" data-src="/static/images/placeholder_400x250.svg"
                                         alt="" v-bind:src="items.imageUrl" data-holder-rendered="true">
                                </div>
                            </div>
                        </template>
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
    name: 'solution',
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
        console.log("created solution")
        this.$store.dispatch('getSolution',{ "method": "getSolution" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted solution")
    },
    methods:{

    }
}
</script>

<style scoped>
section {
    padding-top: 60px;
    padding-bottom: 60px;
}
.panel {
    margin-top: 40px;
}
.panel-heading .panel-title {
    font-size: 30px;
    font-weight: 600;
}
.panel-heading small {
    color: #3099E3;
    font-size: 20px;
    font-weight: 600;
}
.panel .panel-body li {
    line-height: 1.8;
}
.nav-tabs li.active a {
    color: #3099E3;
}
</style>
