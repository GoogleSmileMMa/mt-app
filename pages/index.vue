<template>
  <div class="page-index">
    <el-row>
      <el-col :span="5">
        <menu/>
      </el-col>
      <el-col :span="19"/>
    </el-row>
  </div>
</template>
<script>
	import menu from "@/components/index/menu"
	export default{
		components:{
			menu
		}
	}
</script>
<style lang="scss">
  @import "../assets/css/login/index.scss";
</style>