<template class="bg-gray-100">
	<section class="antialiased text-gray-600 h-screen px-4">
		<div class="flex flex-col justify-center my-20">
			<div
				class="w-full max-w-3xl mx-auto bg-white shadow-lg rounded-sm border border-gray-200"
			>
				<header class="px-5 py-4 border-b border-gray-100 flex justify-between">
					<h2 class="font-semibold text-gray-800">Most starred Github repos</h2>
					<ul class="space-x-2">
						<li
							v-for="page in 10"
							:key="page"
							class="inline-block border border-gray-600 py-0 px-1 rounded"
							:class="currentPage == page ? 'bg-gray-600 text-white' : ''"
						>
							<button @click="changePage(page)">{{ page }}</button>
						</li>
					</ul>
				</header>
				<div class="p-3">
					<div v-for="repo in repos" :key="repo">
						<RepoComponent class="mt-5" :repo="repo" />
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
	import RepoComponent from './components/RepoComponent.vue';
	import axios from 'axios';

	export default {
		components: {
			RepoComponent,
		},

		created() {
			this.getRepos();
		},

		data() {
			return {
				repos: {},
				currentPage: 1,
			};
		},

		methods: {
			getRepos() {
				axios.get(
					'https://api.github.com/search/repositories?q=created:>2017-10-22&sort=stars&order=desc&page=' +
						this.currentPage
				)
					.then((res) => {
						this.repos = res.data.items;
					})
					.catch((error) => console.log(error));
			},
			changePage(page) {
				this.currentPage = page;
				this.getRepos();
			},
		},
	};
</script>
