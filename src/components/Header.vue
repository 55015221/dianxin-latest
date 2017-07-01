<template>
    <header class="header">
        <div class="container">
            <div class="navbar navbar-default">
                <div class="navbar-header">
                    <button class="navbar-toggle" type="button" data-toggle="collapse" data-target="#bs-navbar"
                            aria-controls="bs-navbar" aria-expanded="true">
                        <span class="sr-only">Toggle navigation</span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                        <span class="icon-bar"></span>
                    </button>
                    <router-link to="/" class="navbar-brand" title="深圳典信科技有限公司">
                        <img class="" alt="深圳典信科技有限公司" src="/static/images/logo.jpg"/>
                    </router-link>
                </div>
                <nav id="bs-navbar" class="navbar-collapse collapse" aria-expanded="true">
                    <ul class="nav navbar-nav navbar-right">
                        <li><a target="_blank" href="https://www.basicredit.com/bct" class="btn btn-info" id="sass-login">云平台</a></li>
                    </ul>
                    <ul class="nav navbar-nav navbar-right">
                        <template v-for="(item, index) in menuList">
                            <router-link :to="item.link" tag="li"><a href="">{{ item.label }}</a></router-link>
                        </template>
                    </ul>
                    <!---->
                    
                    
                </nav>
            </div>
        </div>
    </header>
</template>


<script>

export default {
    name: 'header',
    props: ['menuList'],
    data () {
        return {
        }
    },
    components: {
    },
    computed: {
    },
    created () {
        console.log("created header")
    },
    mounted () {
        console.log("mounted header")
    },
    methods:{

    }
}
</script>

<style>

/*
 * Main navigation
 *
 * Turn the `.navbar` at the top of the docs purple.
 */

.header {
    background: #fff;
    /*box-shadow: 1px 1px 8px rgba(0,0,0,.4);*/
}
.navbar-brand {
    height: 80px;
    padding: 10px 15px;
}
.navbar-brand img {
    height: 60px;
}

.navbar {
    border: 0;
    margin: 0;
    background: none;
}
.header .navbar-nav,
.header .navbar-toggle {
    margin-top: 20px;
}
.header .navbar-nav > li{
    font-size: 15px;
}

.header .navbar-nav > li > a {
    color: #333;
    border-bottom: 2px solid #fff;
}

.header .in .navbar-nav > li > a:hover,
.header .in .navbar-nav > .active > a,
.header .in .navbar-nav > .active > a:hover {
    color: #3099E3;
    background: #fff;
}

.header .navbar-nav > li > a:hover,
.header .navbar-nav > .active > a,
.header .navbar-nav > .active > a:hover {
    color: #3099E3;
    border-bottom: 2px solid #3099E3;
}

.header .navbar-toggle .icon-bar {
    background: #444;
}
.header .navbar-header .navbar-toggle {
    border-color: #fff;
}
.header .navbar-header .navbar-toggle:hover,
.header .navbar-header .navbar-toggle:focus {
    background: #f9f9f9;
    border-color: #f9f9f9;
}
.navbar-default .navbar-nav>.active>a,
.navbar-default .navbar-nav>.active>a:focus,
.navbar-default .navbar-nav>.active>a:hover {
    color: #3099E3;
    background: none;
}

#sass-login {
    padding-top: 10px;
    padding-bottom: 10px;
    margin-top: 5px;
    border-bottom: none;
}
#sass-login:hover {
    border-bottom: 1px solid #269abc;
}
</style>
