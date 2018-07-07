<template>
	<div style="margin:auto;width: 50%">
		<p style="font-size: 30px">用户注册页面</p>
		用户名：<el-input v-model="phone" placeholder="请输入内容" style="width: 30%">
		</el-input><br/><br/>
		手机号：<el-input v-model="user" placeholder="请输入内容" style="width: 30%">
		</el-input><br/><br/>
		密&nbsp;&nbsp;&nbsp;&nbsp;码：<el-input v-model="password" placeholder="请输入内容" style="width: 30%"></el-input><br/><br/>
		姓&nbsp;&nbsp;&nbsp;&nbsp;名：<el-input v-model="name" placeholder="请输入内容" style="width: 30%"></el-input><br/><br/>
		<el-button type="success" round @click="register">注册</el-button>
		<el-button type="success" round @click="login">返回登录</el-button>
	</div>
</template>

<script type="text/javascript">
	export  default{
		data(){
			return{
				phone:'',
				user:'',
				password:'',
				name:''
			}
		},
		methods:{
			register(){
				var userinfo={
					"username":this.username,
					"password":this.password,
					"phone":this.phone,
					"name":this.name
				}
				this.axios({
					method:'post',
					url:'apis/regist',
					data:userinfo,
				}).then(response=>{
					if(response.data.code=="0000"){
						this.$router.push({path:'/'})
						this.$message.error("注册成功，请登录")
					}else{
						this.$message.error(response.data.msg)
					}
				})
				
			},
			login(){
			this.$router.push({path:'/login'})
			}
		}
	}
</script>

<style rel="stylesheet">

</style>
