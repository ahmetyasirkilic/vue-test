	<template>
		<div>
			<h1>{{userData.name}}</h1>
			<ul>
				<li>{{userData.email}}</li>
				<li>{{userData.phone}}</li>
				<li>{{userData.website}}</li>
			</ul>

			<router-link :to="postsLink">Posts</router-link>
		</div>
	</template>

	<script>

		export default {
			name: 'UserProfile',
			data() {
				return {
					userData: []
				}
			},
			computed:{
				postsLink(){
					return `/user/${this.$route.params.id}/posts`;
				}
			},
			created(){
				fetch(`https://jsonplaceholder.typicode.com/users/${this.$route.params.id}`)
				.then((res) => { return res.json() })
				.then((data) => { this.userData = data; })
			}
		}
	</script>