	<template>
		<div>
			<router-link :to="userLink">Back to home</router-link>
			<template v-for="post in posts">
				<h4>{{post.title}}</h4>
				<p>{{post.body}}</p>

				<hr />
			</template>
		</div>
	</template>

	<script>
		
		export default {
			name: 'UserPosts',
			data() {
				return {
					posts: []
				}
			},
			computed: {
				userLink(){
					return `/user/${this.$route.params.id}`;
				}
			},
			created(){
				fetch(`https://jsonplaceholder.typicode.com/posts?userId=${this.$route.params.id}`)
				.then((res) => { return res.json() })
				.then((data) => { this.posts = data; })
			}
		}
	</script>