<template>
  <div id="app">
    <img src="./assets/logo.png">
    <!-- <test msg="这是新的属性值!"></test> -->
		<ul>
			<li>
				<router-link to="/">Users</router-link>
				<router-link to="/test">Test</router-link>
			</li>
		</ul>
		<router-view></router-view>
  </div>

</template>

<script>
export default {

}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


