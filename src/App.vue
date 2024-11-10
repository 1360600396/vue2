<template>
  <div id="app">
    <!-- <nav>
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </nav>
    <router-view/> -->
    <HomeViewVue></HomeViewVue>

  </div>
</template>
<script>
import HomeViewVue from './views/HomeView.vue'
export default {
  name: "App",
  components: {
    // 'a-input-search': Input.Search,
		// AMenu: Menu,
    // AMenuItemGroup: Menu.ItemGroup,
    // AMenuItem: Menu.Item,
    // ASubMenu: Menu.SubMenu,
    // AMenuDivider: Menu.Divider,
    // AButton: Button,
    // ATooltip: Tooltip,
    // AModal: Modal,
    HomeViewVue
  },
}
</script>
<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
