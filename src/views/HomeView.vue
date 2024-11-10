<template>
  <div id="app">
    
		<div class="condition-box">
			<div class="title-box">
				<div 
					v-for="(item, index) in titles" 
					:key="index"	
					:class="current == index ? 'active' : ''"
					@click="changeTitle(item, index)"
				>
					{{ item.title }}
					<span> {{ item.subTitle }} </span>
				</div>
			</div>
			<div class="search-box">
				<a-input-search
				  v-model="value"
				  placeholder="input search text"
				  style="width: 200px"
				  @search="onSearch"
				/>
			</div>
		</div>
		<div class="list-box">
			<div class="list-item" v-for="(item, index) in pics" :key="index">
				<div class="list-item-box">
					<div class="tips">{{ item.tips }}</div>
					<img v-lazy='imgUrl' alt="">
					<div class="list-desc">
						<div class="title">{{ item.title }}</div>
						<div class="time">{{ item.time }}</div>
					</div>
				</div>
				<a-dropdown-button @click="handleButtonClick">
      Dropdown
      <a-menu slot="overlay" @click="handleMenuClick">
        <a-menu-item key="1"> <a-icon type="user" />1st menu item </a-menu-item>
        <a-menu-item key="2"> <a-icon type="user" />2nd menu item </a-menu-item>
        <a-menu-item key="3"> <a-icon type="user" />3rd item </a-menu-item>
      </a-menu>
    </a-dropdown-button>
			</div>
		</div>
	
		
  </div>
</template>
<script>
import { Input } from 'ant-design-vue';
import {
  Button,
  Icon,
  Menu,
  Modal,
  Badge,
  message,
  Tooltip,
} from "ant-design-vue";
export default {
  components: {
    'a-input-search': Input.Search,
		AMenu: Menu,
    AMenuItemGroup: Menu.ItemGroup,
    AMenuItem: Menu.Item,
    ASubMenu: Menu.SubMenu,
    AMenuDivider: Menu.Divider,
    AButton: Button,
    ATooltip: Tooltip,
    AModal: Modal,
  
  },
    data() {
			return {
				imgUrl: "https://build.glodonedu.com/oss/image/byid/3574132519423513066",
				titles: [
					{id: 1, title: "软件学习", subTitle: "123"},
					{id: 2, title: "专家课堂", subTitle: "123"},
					{id: 3, title: "直播回顾", subTitle: "123"},
				],
				current: 0,
				value: "", // 搜索框的值
				pics: [
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
					{ id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟"},
				]
			}
		},
		methods: {
			onSearch: function(searchValue){
			  console.log('use value', searchValue);
			  console.log('or use this.value', this.value);
			},
			changeTitle(item, index) {
				this.current = index;
			}
		}
	}
</script>

<style scoped>
*{
	padding: 0;
	margin: 0;
}
#app {
	width: 100%;
	height: 100vh;
}
	.active {
		border: 3px solid blue;
	}
	
	
	.condition-box {
		overflow-x: auto; /* 宽度不足时出现水平滚动条 */
		position: fixed;
		left: 50%;
		transform: translate(-50%, 0);
		overflow: hidden;
		z-index: 999;
		/* position: fixed; */
		max-width: 1200px;
		width: 70%;
		margin:  0 auto;
		height: 80px;
		padding: 0 10px;
		box-sizing: border-box;
		display: flex;
		align-items: center;
		justify-content: space-between;
		margin: 0 auto;
		background-color: blue;
	}
	
	.title-box 	{
		width: 70%;
		display: flex;
		border-radius: 10px;
		
	}
	
	.title-box div {
		width: 160px;
		height: 60px;
		font-size: 20px;
		display: flex;
		align-items: center;
		justify-content: center;
		color: white;
	}
	
	.title-box div span {
		font-size: 12px;
	}
	
	.title-box div:nth-child(1) {
		background-color: #fc6a6b;
	}
	
	
	.title-box div:nth-child(2) {
		background-color: #45cad9;
	}
	.title-box div:nth-child(3) {
		background-color: #f5c45e;
	}
	
	
	.list-box {
		/* margin-left: 5%; */
		padding-top: 80px;
	max-width: 1200px;
	margin: 0 auto;
		width: 70%;
		display: flex;
		flex-wrap: wrap;
		height: calc(100vh - 80px);
		overflow-y: auto; /* 使 box2 内部内容可滚动 */
	}
	.list-item {
		width: 16.66%;
		padding: 10px;
		box-sizing: border-box;
	}
	
	.list-item-box {
		width: 100%;
		border: 1px solid #ccc; 
		border-radius: 10px;
		position: relative;
	}
	
	.tips {
		padding: 4px 12px;
		color: white;
		position: absolute;
		top: 0px;
		right: 0px;
		background-color: deepskyblue;
		border-bottom-left-radius: 10px;
		border-top-right-radius: 10px;
	}
	
	img {
		width: 100%;
		border-top-left-radius: 10px;
		border-top-right-radius: 10px;
		transition: .2s;
	}
	img:hover {
		transform: scale(1.1);
	}
	
	.list-desc {
		display: flex;
		width: 100%;
		height: 40px;
		padding: 0 10px;
		align-items: center;
		justify-content: space-between;
		
		
	}
	
	.title {
		font-size: 14px;
		font-weight: 600;
		width: 70%;
		white-space: nowrap;  /* 强制不换行 */
		overflow: hidden;
		text-overflow: ellipsis;
	}
	
	.time {
		width: 30%;
		font-size: 12px;
	}
	
	/* 当屏幕小于1400px */
	@media screen and (max-width: 1400px){
		/* .list-box {
			width: 25%;
		} */
		.list-item {
			width: 20%;
		}
		
		.tips {
			padding: 4px 8px;
			color: white;
			position: absolute;
			top: 0px;
			right: 0px;
			background-color: deepskyblue;
			border-bottom-left-radius: 10px;
			border-top-right-radius: 10px;
		}
		
		.title {
			font-size: 14px !important;
			width: 60% !important;
		}
		.time {
			font-size: 12px;
			width: 40% !important;
		}
	}
	/* 当屏幕小于1200px */
	@media screen and (max-width: 1200px){
		.list-box {
		}
		.list-item {
			width: 25%;
		}
	}
	
	/* 当屏幕小于992px */
	@media screen and (max-width: 992px){
		.list-box {
		}
		
		/* .list-desc {
			display: flex;
			flex-wrap: wrap;
			
		} */
		.tips {
			padding: 4px 8px;
			font-size: 12px;
			color: white;
			position: absolute;
			top: 0px;
			right: 0px;
			background-color: deepskyblue;
			border-bottom-left-radius: 10px;
			border-top-right-radius: 10px;
		}
		.title {
			font-size: 14px !important;
			width: 100% !important;
		}
		.time {
			font-size: 12px;
			width: 100% !important;
		}
		
		
	}
	/* 当屏幕小于768 */
	@media screen and (max-width: 768px){
		.list-box {
		}
		.list-item {
			width: 33.3%;
		}
	}
	
	
	/* 当屏幕小于700 */
	@media screen and (max-width: 700px){
		.list-box {
			}
		.list-item {
			width: 50%;
		}
		/* .condition-box {
			display: flex;
			flex-wrap: wrap;
			margin: 40px 0;
		}
		.title-box { 
			width: 100%;
		}
		.search-box {
			width: 100%;
			margin-top: 20px;
			
		} */
	}
	
	
</style>
