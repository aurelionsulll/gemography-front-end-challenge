<template>
	<div class="flex space-x-3 items-center">
		<img
			class="rounded w-28 h-28"
			:src="`${repo.owner.avatar_url}`"
			:alt="`${repo.owner.login}`"
		/>
		<div class="space-y-3">
			<h2 class="font-bold text-lg">{{ repo.name }}</h2>
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
						v-show="repo.open_issues_count"
						>Issues: {{ repo.open_issues_count }}</span
					>
				</div>
				<p>
					Submited {{ currentDateTime(repo.created_at) }}
					<span class="font-bold">{{ repo.owner.login }}</span>
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
