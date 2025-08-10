<script setup lang="ts"></script>
<template>
	<!-- classes -->
	<section class="py-10">
		<div class="container">
			<div class="flex justify-center">
				<h2 class="text-2xl lg:text-3xl text-center font-semibold">
					Fanlardan taqdimotlar
				</h2>
			</div>

			<div
				class="mt-5 grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4"
			>
				<ClassCard
					v-for="item in 5"
					:key="item"
					:item="item"
					:url="`/presentation/${item}`"
				/>
			</div>
		</div>
	</section>
	<!-- classes -->
</template>
