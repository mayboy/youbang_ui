<template>
    <div class="login_page fillcontain">
        <transition name="form-fade" mode="in-out">
            <section class="form_contianer" v-show="showLogin">
                <div class="manage_tip">
                    <p>后台管理系统</p>
                </div>
                <el-form :model="loginForm" :rules="rules" ref="loginForm">
                    <el-form-item prop="username">
                        <el-input v-model="loginForm.username" placeholder="用户名"><span>dsfsf</span></el-input>
                    </el-form-item>
                    <el-form-item prop="password">
                        <el-input type="password" placeholder="密码" v-model="loginForm.password"></el-input>
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="submitForm('loginForm')" class="submit_btn">登陆</el-button>
                    </el-form-item>
                    <el-form-item>
                        <el-button type="primary" @click="register('loginForm')" class="submit_btn">注册</el-button>
                    </el-form-item>
                </el-form>
            </section>
        </transition>
    </div>
</template>

<script>

	import {mapActions, mapState} from 'vuex'
    import {baseUrl} from "../config/path";

	const axios = require('axios');

	export default {
		data() {
			return {
				loginForm: {
					username: '',
					password: '',
				},
				rules: {
					username: [
						{required: true, message: '请输入用户名', trigger: 'blur'},
					],
					password: [
						{required: true, message: '请输入密码', trigger: 'blur'}
					],
				},
				showLogin: false,
			}
		},
		mounted() {
			this.showLogin = true;
			if (!this.adminInfo.id) {
				this.getAdminData()
			}
		},
		computed: {
			...mapState(['adminInfo']),
		},
		methods: {
			...mapActions(['getAdminData']),
			async submitForm(formName) {
                  let that=this;
				axios.post(baseUrl+'/admin/login', {
					username: this.loginForm.username,
					password: this.loginForm.password
				}).then(function (response) {

					if (response.data.code == "200") {
						that.$router.push('/manage');
					}
					else {

					    alert("用户或者密码")
                    }
				})
					.catch(function (error) {
						console.log(error);
					});
			},
			register(formName) {
				alert("ddd")
				this.$router.push("/register")
			},

		},

		watch: {
			adminInfo: function (newValue) {
				// if (newValue.id) {
				// 	this.$message({
				//         type: 'success',
				//         message: '检测到您之前登录过，将自动登录'
				//     });
				// 	this.$router.push('manage')
				// }
			}
		}
	}
</script>

<style lang="less" scoped>
    @import '../style/mixin';

    .login_page {
        background-color: #324057;
    }

    .manage_tip {
        position: absolute;
        width: 100%;
        top: -100px;
        left: 0;

        p {
            font-size: 34px;
            color: #fff;
        }
    }

    .form_contianer {
        .wh(320px, 210px);
        .ctp(320px, 210px);
        padding: 25px;
        border-radius: 5px;
        text-align: center;
        background-color: #fff;

        .submit_btn {
            width: 100%;
            font-size: 16px;
        }
    }

    .tip {
        font-size: 12px;
        color: red;
    }

    .form-fade-enter-active, .form-fade-leave-active {
        transition: all 1s;
    }

    .form-fade-enter, .form-fade-leave-active {
        transform: translate3d(0, -50px, 0);
        opacity: 0;
    }
</style>
