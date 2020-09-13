<template>
  <div style="border:1px solid red;">
    <!--  <el-radio-group v-model="isCollapse" style="margin-bottom: 20px;">-->
    <!--    <el-radio-button :label="false">展开</el-radio-button>-->
    <!--    <el-radio-button :label="true">收起</el-radio-button>-->
    <!--  </el-radio-group>-->
    <el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
             :collapse="isCollapse" background-color="#545c64" text-color="white">
      <el-submenu index="1" text-color="#fff" active-text-color="#ffd04b">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span slot="title">导航一</span>
        </template>
        <el-menu-item-group>
          <span slot="title">分组一</span>
          <el-menu-item index="1-1">选项1</el-menu-item>
          <el-menu-item index="1-2">选项2</el-menu-item>
        </el-menu-item-group>
        <el-menu-item-group title="分组2">
          <el-menu-item index="1-3">选项3</el-menu-item>
        </el-menu-item-group>
        <el-submenu index="1-4">
          <span slot="title">选项4</span>
          <el-menu-item index="1-4-1">选项1</el-menu-item>
        </el-submenu>
      </el-submenu>
      <el-menu-item index="2">
        <i class="el-icon-menu"></i>
        <span slot="title">导航二</span>
      </el-menu-item>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>
    <!--   展开 -->
    <div @mouseover="showNav" @mouseout="hideNav" class="unfold"
         style="width: 10px;height: 92.5vh;display: block;float: left;opacity: 0">
      <a href="#" @click="setStatus"><i class="el-icon-arrow-left"
                                        style="height: 92.5vh;line-height: 92.5vh;text-align: center;margin-left:-2px">

                                      </i>
      </a>
    </div>
  </div>
</template>
<script>
const $ = require("jquery");
export default {
  data() {
    return {
      isCollapse: false,
      flag: true
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
    setStatus() {
      this.isCollapse = !(this.isCollapse)
      if (this.isCollapse) {
        $(".unfold a i").attr("class", "el-icon-arrow-right")
      } else {
        $(".unfold a i").attr("class", "el-icon-arrow-left")
      }
    },
    showNav() {
      $(".unfold").animate({"opacity": "1"})
    },
    hideNav() {
      $(".unfold").animate({"opacity": "0"})
    }
  }
}
</script>

<style scoped>
.el-menu {
  text-align: left;
  height: 92.5vh;
  display: block;
  float: left;
}

.el-menu-vertical-demo:not(.el-menu--collapse) {
  width: 200px;
  min-height: 400px;
}

.el-menu-item i {
  color: white !important;
}

.el-submenu__title i {
  color: white;
}



.unfold:hover {
  box-shadow: 2px 0 5px -1px rgb(84, 92, 100);
  display: block;
}
</style>
