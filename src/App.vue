<template>
	<section class="antialiased bg-gray-100 text-gray-600 h-screen px-4">
		<div class="flex flex-col justify-center h-full">
			<div
				class="w-full max-w-2xl mx-auto bg-white shadow-lg rounded-sm border border-gray-200"
			>
				<header class="px-5 py-4 border-b border-gray-100">
					<h2 class="font-semibold text-gray-800">Most starred Github repos</h2>
				</header>
				<div class="p-3">
					<RepoComponent />
				</div>
			</div>
		</div>
	</section>
</template>

<script>
	import axios from 'axios';
	import RepoComponent from '@/components/RepoComponent';

	export default {
		component: {
			RepoComponent,
		},

		created() {
			// this.getRepos()
		},

		data() {
			return {
				repos: {},
			};
		},

		methods: {
			getRepos() {
				axios.get(
					'https://api.github.com/search/repositories?q=created:>2017-10-22&sort=stars&order=desc'
				)
					.then((res) => console.log(res.data.items))
					.catch((error) => console.log(error));
			},
		},
	};
</script>

<style></style>
