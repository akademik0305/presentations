<script setup lang="ts">
const props = defineProps({
	item: {
		type: Number,
		required: true,
	},
	url: {
		type: String,
		required: true,
	},
});
</script>
<template>
	<NuxtLink
		:to="props.url"
		class="bg-white shadow-md rounded-xl p-4 cursor-pointer hover:scale-[1.02] transition-all"
	>
		<div class="rounded-md w-full h-auto">
			<img
				src="~/assets/images/jpg/math.jpg"
				class="w-full h-full object-cover"
				alt="math"
			/>
		</div>

		<div class="mt-4">
			<h3 class="text-2xl text-text text-center">Matematika</h3>
		</div>
	</NuxtLink>
</template>
