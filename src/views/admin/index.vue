<template>
  <section>
    <Topbar />
    <el-container style="height: 100%">
      <el-aside width="200px" style="height: 100%; background-color: #f4f4f5">
        <el-menu :default-active="routeFullPath" background-color="#f4f4f5" router>
          <el-menu-item index="/admin/storages">
            <i class="el-icon-files"></i>
            <span slot="title">存储管理</span>
          </el-menu-item>
          <el-menu-item index="/admin/storage-quota">
            <i class="el-icon-user"></i>
            <span slot="title">{{ $t("title.storage-quota") }}</span>
          </el-menu-item>
          <!-- <el-menu-item index="/admin/settings">
          <i class="el-icon-setting"></i>
          <span slot="title">系统设置</span>
        </el-menu-item> -->
        </el-menu>
      </el-aside>

      <el-main>
        <router-view></router-view>
      </el-main>
    </el-container>
  </section>
</template>

<script>
import Topbar from "@/components/Topbar";
export default {
  components: {
    Topbar,
  },
  data() {
    return {
      routeFullPath: "disk",
    };
  },
  watch: {
    $route(newVal, oldVal) {
      this.routeFullPath = newVal.fullPath;
    },
  },
  mounted() {
    this.routeFullPath = this.$route.fullPath;
  },
};
</script>

<style>
</style>