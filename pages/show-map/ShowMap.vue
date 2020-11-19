
<template>
	<view>
		<map class="map" id="map" :longitude="longitude" :latitude="latitude"
				 scale="16" show-location="true" :markers=markers  bindmarkertap="makertap"></map>
	</view>
</template>

<script>
import amap from '../../libs/amap-wx.js'
	export default {
			data() {
				return {
					amapPlugin: null,
					//高德key，填入步骤1申请的
					key: "	e7a8d95066d5e9811f281eb714f86bbe",
					//点坐标
					markers: [
						{
							//可用本地图片替换
							iconPath: "../../static/img/mapicon_navi_s.png",
							id: 0,
							latitude: 39.989643,
							longitude: 116.481028,
							width: 23,
							height: 33
						}, {
							//可用本地图片替换
							iconPath: "../../static/img/mapicon_navi_e.png",
							id: 0,
							latitude: 39.90816,
							longitude: 116.434446,
							width: 24,
							height: 34
						},
					],
					//中心点
					latitude: 39.989643,
					longitude: 116.481028
				}
			},
			onLoad() {
				this.amapPlugin = new amap.AMapWX({
				key: this.key
				})
				//获取当前位置
				this.amapPlugin.getRegeo({
					//可用本地图片替换
					iconPath: "../../static/img/mapicon_navi_s.png",
					iconWidth: 22,
					iconHeight: 33,
					success: function(data) {
						console.log(data)
					}
				});
			},
			methods: {}
		}
</script>

<style>
#map{
	width: 500px;
	height: 500px;
}
</style>
