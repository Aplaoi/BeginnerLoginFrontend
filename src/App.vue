<script setup>
import {ref,onMounted} from "vue";
import axios from "axios";

const username=ref('');
const password=ref('');

const submitForm = async ()=>{
	const formData={
		username:username.value,
		password:password.value
	};
	try {
		// response是axios获取的对象
		const response=await axios.post("http://localhost:8080/data",formData);
		if (response.status===200&&response.data==="登录成功"){
			alert("nb，这都能登进来");
		}
		else if(response.status===200&&response.data==="登录失败") {
			alert("失败了吧小sb");
		}
	}catch (error){
		console.log("提交失败",error);
	}

};


onMounted(()=>console.log("成功挂载"));
</script>


<template>
	<h1>登录系统</h1>
	<div class="login-form">
		<el-form label-width="auto" style="max-width: 300px">
			<el-form-item label="用户名">
				<el-input v-model="username"></el-input>
			</el-form-item>
			<el-form-item label="密码">
				<el-input v-model="password" v-bind:type="'password'"></el-input>
			</el-form-item>
			<el-form-item>
				<el-button type="primary" @click="submitForm">提交</el-button>
			</el-form-item>
		</el-form>
	</div>



</template>


<style scoped>
h1{
	display: flex;
	justify-content: center;
	font-size: xx-large;
}

.login-form{
	display: flex;
	justify-content: center;
	font-size: xx-large;
}

</style>
