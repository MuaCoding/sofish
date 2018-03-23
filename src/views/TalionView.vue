<template>
	<div class="talion-view">
		<div class="header-bar">
			<span class="close-talion" @click="closeTalion">关闭</span>
			<form class="search" onsubmit="return false">
				<input type="search" name="query" v-model.trim.lazy="queryStr" @key.enter="goSeach()">
			</form>
		</div>
		<ul class="has-header">
			<li>
				<div>
					<a href="#" target="_blank">
						<span style="color: rgb(35, 132, 232);">电影</span>
						<span>影院热映</span>
					</a>
					<a href="#" target="_blank">
						<span style="color: rgb(230, 70, 126);">同城</span>
						<span>周末活动</span>
					</a>
					<a href="#" target="_blank">
						<span style="color: rgb(159, 120, 96);">阅读</span>
						<span>电子书</span>
					</a>
					<a href="#" target="_blank">
						<span style="color: rgb(225, 100, 77);">东西</span>
						<span>心爱之物</span>
					</a>
				</div>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		name:'talion-view',
		componnets: {},
		data(){
			return{
				queryStr: ''
			}
		},
		methods:{
			closeTalion: function(){
				this.$emit('closeTalion')
			},
			goSeach: function(){
				this.$emit('closeTalion')
				this.$router.push({
					name: 'SeachView',
					params: {
						q: this.queryStr
					}
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.talion-view {
		position: fixed;
		top: 0;
		width: 100%;
		height: 100%;
		background-color: #fff;
		z-index: 101;
	}
	.close-talion{
		color: #42bd56;
  		font-size: 1.6rem;
	}

	.search{
		flex: 1;
		width: 100%;
		padding: 1rem;
	}

	input[type=search]{
		box-sizing: border-box;
		border: 0;
		background-size: 1.73rem;
		border-radius: 0.3rem;
		width: 100%;
		height: 3.2rem;
		font-size: 1.4rem;
		padding: 1rem;
		outline: none;
		border-radius: .3rem;
		background-color: #f3f3f3;
	}
</style>