<template>
  <el-menu
    mode="horizontal"
    :router="true">
    <template v-for="(menu, menuIndex) in menus">
      <d2-layout-main-menu-item v-if="menu.children === undefined" :menu="menu" :key="menuIndex"/>
      <d2-layout-main-menu-sub v-else :menu="menu" :key="menuIndex"/>
    </template>
  </el-menu>
</template>

<script>
import menus from '@/menu/index.js'
export default {
  name: 'd2-layout-main-menu-header',
  components: {
    'd2-layout-main-menu-item': () => import('../-menu-item/index.vue'),
    'd2-layout-main-menu-sub': () => import('../-menu-sub/index.vue')
  },
  data () {
    return {
      menus
    }
  }
}
</script>
