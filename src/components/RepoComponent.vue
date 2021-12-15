<template>
	<div class="flex space-x-3 items-center">
		<img class="rounded w-28 h-28" :src="`${repo.owner.avatar_url}`" alt="repo name" />
		<div class="space-y-3">
			<h2>{{ repo.name }}</h2>
			<p class="">
				{{ repo.description }}
			</p>

			<div class="flex justify-between space-x-4">
				<div class="space-x-4">
					<span class="border border-gray-600 px-1 py-1 rounded"
						>Stars: {{ repo.stargazers_count }}</span
					>
					<span
						class="border border-gray-600 px-1 py-1 rounded"
						v-if="repo.open_issues_count"
						>Issues: {{ repo.open_issues_count }}</span
					>
				</div>
				<p>
					Submited {{ currentDateTime(repo.created_at) }}
					{{ repo.owner.login }}
				</p>
			</div>
		</div>
	</div>
</template>

<script>
	import moment from 'moment';

	export default {
		props: {
			repo: Object,
		},
		methods: {
			currentDateTime(date) {
				return moment(date, 'YYYYMMDD').fromNow();
			},
		},
	};
</script>

<style></style>
