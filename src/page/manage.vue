<template>
	<div class="manage_page fillcontain">
		<el-row style="height: 100%;">
	  		<el-col :span="4"  style="min-height: 100%; background-color: #324057;">
				<el-menu :default-active="defaultActive" style="min-height: 100%;" theme="dark" router>
					<el-menu-item index="manage"><i class="el-icon-menu"></i>首页</el-menu-item>
					<el-submenu index="2">
						<template slot="title"><i class="el-icon-document"></i>教师管理</template>
						<el-menu-item index="teacherList">老师列表</el-menu-item>
						<el-menu-item index="teacherAdd">添加老师</el-menu-item>
					</el-submenu>
                    <el-submenu index="3">
                        <template slot="title"><i class="el-icon-plus"></i>添加数据</template>
                        <el-menu-item index="addShop">添加商铺</el-menu-item>
                        <el-menu-item index="addGoods">添加商品</el-menu-item>
                    </el-submenu>
					<el-submenu index="4">
                    <template slot="title"><i class="el-icon-plus"></i>公众号管理</template>
                    <el-menu-item index="wxUserList">用户列表</el-menu-item>
                    <el-menu-item index="wxUserMessage">发送消息</el-menu-item>
                </el-submenu>
                    <el-submenu index="5">
                        <template slot="title"><i class="el-icon-star-on"></i>消息管理</template>
                        <el-menu-item index="messageList">消息模板列表</el-menu-item>
                        <el-menu-item index="messageAdd">添加消息模板</el-menu-item>
                        <el-menu-item index="messageEdit">编辑消息模板</el-menu-item>
                    </el-submenu>


					<el-submenu index="6">
						<template slot="title"><i class="el-icon-edit"></i>编辑</template>
						<!-- <el-menu-item index="uploadImg">上传图片</el-menu-item> -->
						<el-menu-item index="vueEdit">文本编辑</el-menu-item>
					</el-submenu>
					<el-submenu index="7">
						<template slot="title"><i class="el-icon-setting"></i>系统管理</template>
						<el-menu-item index="adminSet">管理员设置</el-menu-item>
						<!-- <el-menu-item index="wxUserMessage">发送通知</el-menu-item> -->
					</el-submenu>
					<el-submenu index="8">
						<template slot="title"><i class="el-icon-warning"></i>说明</template>
						<el-menu-item index="explain">说明</el-menu-item>
					</el-submenu>
				</el-menu>
			</el-col>
			<el-col :span="20" style="height: 100%;overflow: auto;">
<!--				<keep-alive>-->
<!--				</keep-alive>-->
                <router-view></router-view>
            </el-col>
		</el-row>
  	</div>
</template>

<script>
    export default {
		computed: {
			defaultActive: function(){
				return this.$route.path.replace('/', '');
			}
		},
    }
</script>


<style lang="less" scoped>
	@import '../style/mixin';
	.manage_page{

	}
</style>
