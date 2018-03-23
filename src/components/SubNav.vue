<template>
	<div class="sub-nav">
		<div class="navBotttom" v-if="mold === 'navBottom'">
			<div class="nav-item">
				<router-link :to="{name: 'RegisterView'}">注册帐号</router-link>
				<!-- <template>
					<a href="#" @click.prevent="logout()">退出登录</a>
				</template> -->
				<template>
					<router-link :to="{name: 'LoginView'}" replace>登录豆瓣</router-link>
				</template>
			</div>
			<div class="nav-item">
				<a href="https://movie.douban.com/">使用桌面版</a>
				<a href="#">使用豆瓣App</a>
			</div>
		</div>
		<div class="quickNav" v-if="mold === 'quickNav'">
			<ul class="quick-nav">
				<li>
					<router-link :to="{name: 'MovieView'}">影院热映</router-link>
				</li>
				<li>
					<router-link :to="{name: 'StatusView'}">欧美新碟榜</router-link>
				</li>
				<li>
					<router-link :to="{name: 'RegisterView'}">注册帐号</router-link>
				</li>
				<li>
					<!-- <template>
						<a href="#" @click.prevent="logout()">退出登录</a>
					</template>
					<template v-else>
						<router-link :to="{name: 'LoginView'}" replace>登录豆瓣</router-link>
					</template> -->
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
	import { mapGetters } from 'vuex'
	export default{
		name:'sub-nav',
		props: {
			mold: {
				type: String,
				default: 'quickNav'
			}
		},
		data(){
			return {}
		},
		computed: {
			currentLink: function(){
				return this.currentUser.name ? 'StatusView' : 'LoginView'
			},
			holder: function(){
				return this.currentUser.name ? this.currentUser.name : '请先登录'
			},
			...mapGetters(['currentUser'])
		},
		methods: {
			logout(){
				this.$store.commit({
					type: 'logout'
				})
				this.$router.push({name: 'HomeView'})
			}
		},
		created(){
			if (localStorage.getItem('email')) {
				this.$store.commit({
			        type: 'getLocalUser'
			    })
			}
		}
	}
</script>

<style lang='scss' scoped>
	.navBotttom{
		width: 100%;
		border-bottom: 0.1rem solid #f3f3f3;

		.nav-item{
			width: 100%;
			border-top: 0.1rem solid #f3f3f3;
			padding: 1.3rem 0;
			text-align: center;
		}

		a{
			width: 50%;
			display: inline-block;
			box-sizing: border-box;
			font-size: 1.5rem;
			color: #42bd56;

			&:first-child{
				border-right: 0.1rem solid #e5e5e5;
			}
		}
	}
</style>