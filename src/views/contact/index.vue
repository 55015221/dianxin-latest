<template>
    <div class="template-wrapper">

        <div style="background: #3099E3 url('/static/images/首页_02.png');margin: 0;">
            <div class="" style="width:1500px; margin:0 auto;">
                <img class="first-slide" src="/static/images/解决方案_02.png" alt="First slide">
            </div>
            <!--
            <div class="jumbotron wow zoomIn">
                <div class="container text-center">
                    <h2>关于我们</h2>
                </div>
            </div>
            -->
        </div>

        <!--content-->
        <section class="content">
            <div class="container">
               <h2>CONTACT US</h2>
               <div class="row">
                    <div class="col-sm-6">
                        <span class="glyphicon glyphicon-phone fa-1x" aria-hidden="true"></span>
                        电话：{{ records.telephone }}
                    </div>
                    <div class="col-sm-6">
                        <span class="glyphicon glyphicon-envelope fa-1x" aria-hidden="true"></span>
                        邮箱：<a :href="'mailto:'+ records.cooperateEmail">{{ records.cooperateEmail }}</a>
                    </div>

                    <div class="col-sm-6">
                        <span class="fa fa-qq fa-1x"></span>
                        客服：{{ records.qq }}
                    </div>
                    <div class="col-sm-6">
                        <span class="fa fa-qq fa-1x"></span>
                        地址：{{ records.address }}
                    </div>
               </div>
               <!--百度地图容器-->
               <div style="height:300px;font-size:12px" id="map"></div>
            </div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'
export default {
    name: 'contact',
    data () {
        return {
            map:{},
        }
    },
    components: {
    },
    computed: {
        ...mapState({
            records: state => state.module.records
        })
    },
    created () {
        console.log("created contact")
        this.init()
        this.$store.dispatch('getContact',{ "method": "getProduct" }).then((res) => {

        })
    },
    mounted () {
        console.log("mounted contact")
        this.initMap()
    },
    methods: {
        loadJScript:function() {
            let script = document.createElement("script");
            script.type = "text/javascript";
            script.src = this.mapApi;
            document.body.appendChild(script);
        },
        init: function () {
            let url = 'http://api.map.baidu.com/api?v=2.0&ak=GdiubtoGrE6Yoi049kuBG87m'
            let script = document.createElement('script')
            script.setAttribute('src', url)
            document.getElementsByTagName('head')[0].appendChild(script)
        },
        initMap:function(){
            this.createMap();//创建地图
            this.setMapEvent();//设置地图事件
            this.addMapControl();//向地图添加控件
            this.addMapOverlay();//向地图添加覆盖物
        },
        createMap:function(){
            this.map = new BMap.Map("map");
            this.map.centerAndZoom(new BMap.Point(114.240383,22.692659),16)
        },
        setMapEvent:function(){
            this.map.enableKeyboard();
            this.map.enableDragging();
        },
        addClickHandler:function(target,window){
            target.addEventListener("click",function(){
                target.openInfoWindow(window);
            });
        },
        addMapOverlay:function(){
            let markers = [
                    {content:"地址：深圳市龙龙岗区大运软件小镇54栋306",title:"深圳市典信科技有限公司",imageOffset: {width:0,height:3},position:{lat:22.691726,lng:114.235883}}
                ];
            for(let index = 0; index < markers.length; index++ ){
                let point = new BMap.Point(markers[index].position.lng,markers[index].position.lat);
                let marker = new BMap.Marker(point,{icon:new BMap.Icon("http://api.map.baidu.com/lbsapi/createmap/images/icon.png",new BMap.Size(20,25),{
                  imageOffset: new BMap.Size(markers[index].imageOffset.width,markers[index].imageOffset.height)
                })});
                let label = new BMap.Label(markers[index].title,{offset: new BMap.Size(25,5)});
                let opts = {
                      width: 200,
                      title: markers[index].title,
                      enableMessage: false
                };
                let infoWindow = new BMap.InfoWindow(markers[index].content,opts);
                marker.setLabel(label);
                this.addClickHandler(marker,infoWindow);
                this.map.addOverlay(marker);
            };
        },
        addMapControl:function(){
            let navControl = new BMap.NavigationControl({anchor:BMAP_ANCHOR_TOP_LEFT,type:BMAP_NAVIGATION_CONTROL_LARGE});
            this.map.addControl(navControl);
        }
    }
}
</script>

<style scoped>
.content h2 {
    margin-top: 60px;
    margin-bottom: 30px;
    color: #3099E3;
    text-align: center;
}
.content .row {
    margin-bottom: 30px;
}
.content .row .col-sm-6 {
    text-indent: 40px;
    font-size: 18px;
    padding: 10px 0;
}
.content .row .col-sm-6 span {
    color: #3099E3;
}
.contact-icon {

}
.contact-icon p {
    margin-top: 15px;
}
.contact-icon .thumbnail {
    cursor: pointer;
    background: none;
    border:none;
}
.contact-icon .thumbnail:hover {
    color: #39f;
}

</style>
