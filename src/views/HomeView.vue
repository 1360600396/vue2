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
      <a-row :gutter="16">
        <a-col 
          v-for="(item, index) in pics" 
          :key="index"
          :xs="24" 
          :sm="12" 
          :md="8" 
          :lg="6" 
          :xl="4"
        >
          <div class="list-item">
            <div class="list-item-box">
              <div class="tips">{{ item.tips }}</div>
              <img v-lazy="imgUrl" alt="" width="100%" height="auto" />
              <div class="list-desc">
                <div class="title">{{ item.title }}</div>
                <div class="time">{{ item.time }}</div>
              </div>
            </div>
          </div>
        </a-col>
      </a-row>
    </div>
  </div>
</template>

<script>
import { Input } from 'ant-design-vue';
import { Button, Icon, Menu, Modal, Badge, message, Tooltip } from "ant-design-vue";

export default {
  components: {
    'a-input-search': Input.Search,
    AMenu: Menu,
    AMenuItem: Menu.Item,
    ASubMenu: Menu.SubMenu,
    AButton: Button,
    ATooltip: Tooltip,
    AModal: Modal,
    ADropdownButton: Button.Group,
    AIcon: Icon
  },
  data() {
    return {
      imgUrl: "https://build.glodonedu.com/oss/image/byid/3574132519423513066",
      titles: [
        { id: 1, title: "软件学习", subTitle: "123" },
        { id: 2, title: "专家课堂", subTitle: "123" },
        { id: 3, title: "直播回顾", subTitle: "123" },
      ],
      current: 0,
      value: "", // 搜索框的值
      pics: [
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
        { id: 1, title: "9期-方圆-群体工程穿插施工分析及进度管理", tips: "小标签", time: "时长：30分钟" },
      ]
    };
  },
  methods: {
    onSearch(searchValue) {
      console.log('use value', searchValue);
      console.log('or use this.value', this.value);
    },
    changeTitle(item, index) {
      this.current = index;
    },
    handleButtonClick() {
      console.log('Dropdown button clicked');
    },
    handleMenuClick() {
      console.log('Menu item clicked');
    }
  }
};
</script>

<style lang="less" scoped>
/* Reset margin and padding for html and body */
html, body {
  margin: 0;
  padding: 0;
  height: 100%;
  font-family: Arial, sans-serif;
}

/* Apply box-sizing for all elements */
*,
*::before,
*::after {
  box-sizing: border-box;
}

#app {
  display: flex;
  flex-direction: column;
  height: 100%;
  overflow: auto; /* Ensure scrollable content in case of overflow */
}

.condition-box {
  margin: 0 auto;
  background-color: #f4f7fc;
  max-width: 1200px;
  height: 56px;
  display: flex;
  justify-content: space-between;
  overflow: hidden; /* Prevent overflow */
}

.title-box {
  display: flex;
}

.title-box > div {
  width: 192px;
  margin-right: 12px;
  justify-content: space-between;
  font-size: 17px;
  display: flex;
  color: white;
  border-radius: 8px;
}

.active {
  border: 1px solid #00BAA0;
  border-radius: 8px;
}

.search-box {
  display: flex;
  border-radius: 8px;
  padding: 10px 16px;
  width: 25%;
  min-width: 200px;
  height: 56px;
  background: #FFFFFF;
  justify-content: center;
}

.list-box {
  max-width: 1200px;
  margin: 0 auto;
  margin-top: 30px;
  flex: 1; /* Allow the list-box to take available space */
  overflow-y: auto; /* Enable vertical scroll when content exceeds container height */
  height: calc(100vh - 120px); /* Ensure list-box fits and provides scrolling */
}

.list-item {
  padding: 10px;
  border-radius: 8px !important;
  box-sizing: border-box;
  overflow: hidden;
  padding-right: 26px;
}

.list-item-box {
  height: 100%;
  width: 100%;
  position: relative;
}

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
  font-size: 12px;
}

.list-desc {
  display: flex;
  width: 100%;
  margin-top: 13px;
  height: 22px;
  justify-content: flex-end;
}

.title {
  font-size: 10px;
  font-weight: 600;
  width: 70%;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.time {
  margin-right: 12px;
  height: 20px;
  width: 31px;
  font-size: 12px;
  line-height: 20px;
  color: #64748B;
}

/* Custom scrollbar styles */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-thumb {
  background-color: #00BAA0;
  border-radius: 10px;
}

::-webkit-scrollbar-track {
  background: #f4f7fc;
}
</style>
