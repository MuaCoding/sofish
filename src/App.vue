<template>
  <div id="app">
    <router-view class="view"></router-view>
    <router-view class="view" name="subject"></router-view>
    <router-view class="view" name="search"></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
html{
	font-size: 62.5%;
}
#app{
	max-width:41.2rem;
	margin: 0 auto;
}

.has-harder{
	margin-top: 4.8rem;
}
h2{
	font-size: 1.68rem;
	font-weight: normal;
	color: #111;
}
ul, li, a, h2 {
  margin: 0;
  padding: 0;
}
li {
  list-style: none;
}

a {
  text-decoration: none;
}

.header-bar{
	position: fixed;
	left: 0;
	right: 0;
	top: 0;
	z-index: 100;
	display: flex;
	align-items: center;
	height: 4.8rem;
	padding: 0 1.8rem;
	background-color: #fff;
	border-bottom: 0.1rem solid #f3f3f3;
}
</style>
