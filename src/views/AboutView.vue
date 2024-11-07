<template>
  <a-dropdown>
    <a-menu slot="overlay" @click="handleMenuClick">
      <a-menu-item key="1">
        <a-icon type="user" />1st menu item
      </a-menu-item>
      <a-menu-item key="2">
        <a-icon type="user" />2nd menu item
      </a-menu-item>
      <a-menu-item key="3">
        <a-icon type="user" />3rd item
      </a-menu-item>
    </a-menu>
    <a-button style="margin-left: 8px">
      {{ selectedMenuText }} <a-icon type="down" />
    </a-button>
  </a-dropdown>
</template>

<script>
import { Dropdown, Menu, MenuItem, Icon, Button } from 'ant-design-vue';

export default {
  components: {
    Dropdown,
    Menu,
    MenuItem,
    Icon,
    Button,
  },
  data() {
    return {
      selectedMenuText: 'Select an option', // 默认文本
    };
  },
  methods: {
    handleMenuClick(e) {
      const { key } = e; // 获取点击的菜单项的 key

      // 更新按钮文本
      const menuItems = {
        1: '1st menu item',
        2: '2nd menu item',
        3: '3rd item',
      };
      this.selectedMenuText = menuItems[key];

      // 根据点击的菜单项执行不同的操作
      switch (key) {
        case '1':
          this.handleFirstOption();
          break;
        case '2':
          this.handleSecondOption();
          break;
        case '3':
          this.handleThirdOption();
          break;
        default:
          break;
      }
    },

    // 定义每个菜单项对应的方法
    handleFirstOption() {
      console.log('1');
      // 在这里写你处理第一个选项的逻辑
    },
    handleSecondOption() {
      console.log('2');
      // 在这里写你处理第二个选项的逻辑
    },
    handleThirdOption() {
      console.log('3');
      // 在这里写你处理第三个选项的逻辑
    },
  },
};
</script>

<style>
@import 'ant-design-vue/dist/antd.css';
</style>
