<template>
	<div class="users">
		<h1>Users</h1>
	
		<!-- 添加用户信息 -->
		<form v-on:submit="addUser">
			<input type="text" v-model="newUser.name" placeholder="Enter name">
			<input type="text" v-model="newUser.email" placeholder="Enter email">
			<input type="submit" value="Submit">
		</form>

		<!-- 展示用户信息 -->
		<ul>
			<li v-for="user in users"  :key="user.email">
				<input type="checkbox" class="toggle" v-model="user.contacted">
				<span :class="{contacted:user.contacted}">
					{{user.name}} : {{user.email}}
					<button v-on:click="deleteUser(user)">x</button>
				</span>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name: "users",
		data(){
			return {
				newUser:{},
				users:[
					{
						name:"张三",
						email:"hemiah@gmail.com",
						contacted:false
					},
					{
						name:"李四",
						email:"henry@gmail.com",
						contacted:false
					},
					{
						name:"王五",
						email:"emily@gmail.com",
						contacted:false
					}
				]
			}
		},
		methods:{
			addUser:function(e) {
				// console.log("hello");
				this.users.push({
					name:this.newUser.name,
					email:this.newUser.email,
					contacted:false
				});
				e.preventDefault();
			},
			deleteUser:function(user){
				// console.log("hello");
				this.users.splice(this.users.indexOf(user),1);
			}
		},
		created:function(){
			// console.log("Hello World!!!!!!");
			this.$http.get("https://jsonplaceholder.typicode.com/users")
				.then(function(response){
					console.log(response.data);
					this.users = response.data;
				})
		}
	}
</script>

<style scoped>
	.contacted{
		text-decoration: line-through;
	}
</style>