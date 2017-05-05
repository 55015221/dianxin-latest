<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="container">
                <h2>What is your problem?</h2>
                <div class="panel-group" id="accordion" role="tablist" aria-multiselectable="true">
                   <template v-for="(item, index) in records">
                      <div class="panel">
                          <div class="panel-heading" role="tab" v-bind:id="'headingOne-' + index">
                            <h4 class="panel-title">
                              <span class="glyphicon glyphicon-plus"></span>
                              <a role="button" data-toggle="collapse" data-parent="#accordion" v-bind:href="'#collapseOne-' + index" v-bind:aria-expanded="(index === 0)?true:false" v-bind:aria-controls="'collapseOne-' + index">
                                {{ item.title }}
                              </a>
                            </h4>
                          </div>
                          <div v-bind:id="'collapseOne-' + index" v-bind:class="(index === 0)?'panel-collapse collapse in':'panel-collapse collapse'" role="tabpanel" v-bind:aria-labelledby="'headingOne-' + index">
                            <div class="panel-body">{{ item.content }}</div>
                          </div>
                        </div>
                  </template>
                </div>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'
import Jumbotron from '../../components/Jumbotron.vue'

export default {
    name: 'questions',
    data () {
        return {
            open: false,
            isOpened: false
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
        console.log("created questions")
        this.$store.dispatch('getQuestions',{ "method": "getQuestions" }).then((res) => {
            console.log(res)
        })
    },
    mounted () {
        console.log("mounted questions")
    },
    methods:{

    }
}
</script>

<style scoped>

.content h2 {
    margin-top: 60px;
    margin-bottom: 60px;
    color: #3099E3;
    font-size: 42px;
    text-align: center;
}
.panel-group .panel+.panel {
    margin-top: 0;
}
.panel .panel-title span {
    color: #3099E3;
}
.panel .panel-body {
    margin-left: 22px;

}
.panel-group .panel-heading+.panel-collapse>.list-group, .panel-group .panel-heading+.panel-collapse>.panel-body {
    border-top: none;
}
</style>
