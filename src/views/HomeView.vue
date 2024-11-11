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

<style lang="less" scoped>
.box {
 height: 100vh;
}
.banma-warp {
margin-top: 24px;
//   padding-top: 24px;
//   padding-left: 7%;
//   padding-bottom: 24px;
 margin-bottom: 24px;
//   padding-right: 11px;
 margin-right: 11px;
 background-color: #F4F7FC;
				 
}
.condition-box {
 margin: 0 auto;
 background-color: #f4f7fc;
 max-width: 1200px;
 height: 56px;
 // padding: 10px 20px;
 box-sizing: border-box;
 display: flex;
 
 justify-content: space-between;
 // padding: 5px 5px;
 .title-box {
	 display: flex;
	 // border-radius: 10px;
	 justify-content: flex-start;
	 // width: 68.835%;
	 // flex-wrap: wrap;
	 .selected-color-0 {
		 cursor: pointer !important;
		 cursor: default;  
		 user-select: none;
		 color: #FFFFFF !important;
		 background: linear-gradient(287deg, #FFB068 0%, #FF8F55 100%) !important;
	 }
	 .selected-color-1 {
		 cursor: pointer !important;
		 cursor: default;  
		 user-select: none;
		 color: #FFFFFF !important;
		 background: linear-gradient(106deg, #3898FF -1%, #75CCFF 99%) !important;
	 }
	 .selected-color-2 {
		 cursor: pointer !important;
		 cursor: default;  
		 user-select: none;
		 color: #FFFFFF !important;
		 background: linear-gradient(104deg, #00D9C3 0%, #4AF7F7 99%) !important;
	 }
	 .title-box1 {
		 display: flex;
		 flex-direction: column;
		 justify-content: center;
		 align-items: flex-start;
	 }
	 
	 >div {
		 // padding: 12px 0px ;
		 box-sizing: border-box;
		 width: 192px;
		 margin-right: 12px;
		 justify-content: space-between;
		 font-size: 17px;
		 display: flex;
		 // align-items: center;
		 // justify-content: center;
		 color: white;
		 border-radius: 8px;

		 &:nth-child(1) {
			 cursor: pointer !important;
		 cursor: default;  
		 user-select: none;
			 color: #EA8735;
			 background: #FFE2C7;
			 background-color: #FFE2C7;
		 }
		 &:nth-child(2) {
			 cursor: pointer !important;
		 cursor: default;  
		 user-select: none;
			 color: #217EEE;
			 background-color: #C3E7FC;
			 background: #C3E7FC;
			 
		 }
		 &:nth-child(3) {
			 cursor: pointer !important;
		 cursor: default;  
		 user-select: none;
			 color: #35B79F;
			 background: #C9FFF3;
			 
		 }
		 &:nth-child(4) {
			 width: 224px;
			 background-color: #00D9C3;
		 }
		 .title-box1 {
			 cursor: default; /* 确保光标是默认的箭头 */
			 user-select: none; /* 禁用文本选择，避免显示选择光标 */
			 flex: 1;
			 // background-color: red;
			 margin: 6px 0 6px 16px;
			 cursor: default; /* 确保光标是默认的箭头 */
				 user-select: none; /* 禁用文本选择，避免显示选择光标 */
			 .title-boxfont1{
				 font-family: HarmonyOS Sans SC;
				 font-size: 18px;
				 font-weight: 500;
	 line-height: 24px;
				 display: block;
				 height: 24px;
				 // color: #EA8735;
				 cursor: default; /* 确保光标是默认的箭头 */
				 user-select: none; /* 禁用文本选择，避免显示选择光标 */
			 }
			 .title-boxfont2 {
				 display: block;
				 height: 20px;
				 line-height: 20x;
				 font-weight: 300;
				 // color: #EA8735;
				 font-size: 12px;
				 font-family: HarmonyOS Sans SC;
				 cursor: default; /* 确保光标是默认的箭头 */
				 user-select: none; /* 禁用文本选择，避免显示选择光标 */
			 }
			 img {
				 cursor: default; /* 确保光标是默认的箭头 */
				 user-select: none; /* 禁用文本选择，避免显示选择光标 */
			 }
		 }
	 }
 
 }
 .active {
	 border: 1px solid #00BAA0;
	 border-radius: 8px;
 }
.search {
display: flex;
border-radius: 8px;
padding: 10px 16px;
width: 25%;
min-width: 200px;
height: 56px;
background: #FFFFFF;
justify-content: center;
position: relative;
//   margin-right: 100px;
input {
//  flex: 1;
border: 0;
width: 100%;
height: 36px;
/* 去掉表单控件的焦点框 */
outline: none;
border: 1px solid #E2E8F0;
box-sizing: border-box;
padding: 7px 16px;
border-radius: 4px;
}
input::placeholder {
font-family: HarmonyOS Sans SC;
font-size: 14px;
font-weight: normal;
line-height: 22px;
letter-spacing: 0em;

font-variation-settings: "opsz" auto;
/* Greyscale/500 */
/* 样式描述：单位及小字说明色 */
color: #96A0B5;
}
a {
position: absolute;
right: 32px;
align-self: center;
width: 16px;
height: 16px;
background-color: #fff;

}
}



/* ::placeholder 选中就是 placeholder 属性文字样式*/


/* 父级是flex布局，子级变弹性盒子：加宽高生效 */



}
// .search-box {
// 		width: 100%;
// 		margin-top: 20px;
	 
// 	}
.list-box {

 max-width: 1200px;
 display: flex;
 flex-wrap: wrap;
 margin: 0 auto;
margin-top: 30px;
// padding-right: 11px;
justify-content: flex-start;
// padding-left: 16px;
// margin-left:5%
height: calc(100vh - 56px);
overflow-y: auto; /* 使 box2 内部内容可滚动 */

}
.list-item {
// width: 16.67%;
// height: 196px;
// border-radius: 8px !important;
// overflow: hidden;
//  background: #FFFFFF;
//  padding: 0px 0px 12px 0px;
// //   margin-right: 24px;
// margin-bottom: 24px;
//  box-sizing: border-box;



width: calc(16.67% - 17px); /* 减去间距 */
 height: 196px;
		padding: 10px;
		border-radius: 8px !important;
		box-sizing: border-box;
		overflow: hidden;
		  margin-right: 16px;
margin-bottom: 24px;
 padding: 0px 0px 12px 0px;
 .list-item-box {
height: 100%;
	 width: 100%;
	 overflow: hidden;
	 position: relative;
	 .tips {
		 box-sizing: border-box;
		 width: 84px;
		 height: 24px;
		 padding: 2px 8px;
		 border-radius: 0px 8px 0px 16px;
		 color: white;
		 position: absolute;
		 top: 0px;
		 right: -8px;
		 background-color: deepskyblue;
		 


		 display: flex;
		 align-items: center;
		 font-family: HarmonyOS Sans SC;
		 font-size: 12px;
		 font-weight: normal;
		 line-height: 20px;
		 letter-spacing: 0em;
		 color: #FFFFFF;
	 }
	 
	 .logo {
	width: 16px;
	height: 16px;
	margin-right: 4px;
}
	span{
	 font-family: HarmonyOS Sans SC;
	 font-size: 12px;
	 font-weight: normal;
	 line-height: 20px;
	 color: #FFFFFF;
	}
	 
	 .list-desc {
		 display: flex;
		 width: 100%;
		 margin-top: 13px;
		 height: 22px;
 justify-content: flex-end;
		 
		 
		 .title {
			 font-size: 10px;
			 font-weight: 600;
			 width: 70%;
			 white-space: nowrap;  /* 强制不换行 */
			 overflow: hidden;
			 text-overflow: ellipsis;
		 }
		 .time {
			 margin-right: 12px;
			 height: 20px;
			 width: 31px;
			 font-family: HarmonyOS Sans SC;
			 font-size: 12px;
			 line-height: 20px;
			 color: #64748B;
		 }
	 }
 }
 
}

/* 当屏幕小于1400px */
// 1742
@media screen and (min-width: 1981px){

}
@media screen and (max-width: 1400px){

}
/* 当屏幕小于1200px */
@media screen and (max-width: 1740px){
// 		.list-item {
 
// 		&:nth-of-type(5n){
// 			margin-right: 24px;
// 		}
// }
}

/* 当屏幕小于992px */
@media screen and (max-width: 992px){
 
 
 
}
/* 当屏幕小于768 */
@media screen and (max-width: 768px){

}


/* 当屏幕小于700 */
@media screen and (max-width: 700px){

}


</style>