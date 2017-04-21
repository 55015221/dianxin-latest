<template>
    <div class="template-wrapper">

        <Jumbotron/>

        <!--content-->
        <section class="content">
            <div class="container">
               <h2>CONTACT US</h2>
                <div class="col-sm-5 col-sm-offset-1">
                    <span class="glyphicon glyphicon-phone-alt"></span>
                    电话：{{ records.telephone }}
                </div>
                <div class="col-sm-5 col-sm-offset-1">
                    <span class="glyphicon glyphicon-envelope fa-1x" aria-hidden="true"></span>
                    邮箱：<a :href="'mailto:'+ records.cooperateEmail">{{ records.cooperateEmail }}</a>
                </div>

                <div class="col-sm-5 col-sm-offset-1">
                    <span class="fa fa-qq fa-1x"></span>
                    客服：{{ records.qq }}
                </div>
                <div class="col-sm-5 col-sm-offset-1">
                    <span class="glyphicon glyphicon-map-marker"></span>
                    地址：{{ records.address }}
                </div>
               <!--百度地图容器-->
            </div>

        </section>
        <section class="baiduMap">
            <div class="container" style="height:300px;" id="map"></div>
        </section>
    </div>
</template>


<script>

import { mapState } from 'vuex'
import Jumbotron from '../../components/Jumbotron.vue'
export default {
    name: 'contact',
    data () {
        return {
            map:{},
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


section {
    padding-top: 60px;
    padding-bottom: 60px;
}

.content h2 {
    margin-bottom: 30px;
    color: #3099E3;
    font-size: 38px;
    text-align: center;
}

.content .col-sm-5 {
    font-size: 18px;
    padding: 10px 0;
}
.content .col-sm-5 span {
    color: #3099E3;
}
.contact-icon {

}
.contact-icon p {
    margin-top: 15px;
}

</style>
