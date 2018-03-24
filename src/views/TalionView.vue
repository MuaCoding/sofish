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
						<strong style="color: rgb(35, 132, 232);">电影</strong>
						<span>影院热映</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(230, 70, 126);">同城</strong>
						<span>周末活动</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(159, 120, 96);">阅读</strong>
						<span>电子书</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(225, 100, 77);">东西</strong>
						<span>心爱之物</span>
					</a>
				</div>
			</li>
			<li>
				<div>
					<a href="#" target="_blank">
						<strong style="color: rgb(122, 106, 219);">电视</strong>
						<span>正在热播</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(42, 184, 204);">小组</strong>
						<span>志趣相投</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(87, 116, 197);">游戏</strong>
						<span>虚拟世界</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(64, 207, 169);">FM</strong>
						<span>红心歌单</span>
					</a>
				</div>
			</li>
			<li>
				<div>
					<a href="#" target="_blank">
						<strong style="color: rgb(159, 120, 96);">图书</strong>
						<span>畅销排行</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(244, 143, 46);">音乐</strong>
						<span>新碟榜</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(89, 108, 221);">应用</strong>
						<span>玩手机</span>
					</a>
					<a href="#" target="_blank">
						<strong style="color: rgb(66, 189, 86);">市集</strong>
						<span>购买原创</span>
					</a>
				</div>
			</li>
		</ul>
		<sub-nav mold="navBottom"></sub-nav>
	</div>
</template>

<script>
	import SubNav from '../components/SubNav'
	export default {
		name:'talion-view',
		components: { SubNav },
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

	ul{
		display: flex;
	  	justify-content: space-around;
	  	padding-top: 2.5rem;
	  	li{
	  		width: 33.33%;
	  	}

	  	div{
	  		position: relative;
	  		float: left;
	  		left: 50%;
	  		top: 0;
	  	}
	  	a{
	  		position: relative;
	  		left: -50%;
	  		top: 0;
	  		display: block;
	  		margin-bottom: 2.5rem;
	  		text-align: center;
	  	}

	  	strong {
	  		display: block;
	  		font-weight: 400;
	  		font-size: 2.4rem;
	  		line-height: 2.8rem;
	  	}
	  	span{
	  		display: block;
	  		color: #999;
	  		height: 1.7rem;
	  		font-size: 1.2rem;
	  		letter-spacing: 0.1rem;
	  	}
	}
</style>