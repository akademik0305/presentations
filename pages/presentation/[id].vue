<script setup lang="ts">
import type { AccordionItem } from "@nuxt/ui";

const items = ref<AccordionItem[]>([
	{
		label: "Icons",
		icon: "i-lucide-smile",
		content: "You have nothing to do, @nuxt/icon will handle it automatically.",
	},
	{
		label: "Colors",
		icon: "i-lucide-swatch-book",
		content:
			"Choose a primary and a neutral color from your Tailwind CSS theme.",
	},
	{
		label: "Components",
		icon: "i-lucide-box",
		content:
			"You can customize components by using the `class` / `ui` props or in your app.config.ts.",
	},
]);
</script>
<template>
	<main class="py-10">
		<section class="container">
			I'm working

			{{ $route.params.id }}
			<div class="flex gap-4">
				<div class="w-80">
					<UAccordion :items="items" />
				</div>
				<div class="w-full rounded-xl overflow-hidden">
					<iframe
						loading="lazy"
						title="prezentation"
						src="https://www.canva.com/design/DAGuWwZEdJU/RQfLIsWA_MXP1JEMm5mONw/view?embed"
						allowfullscreen
						allow="fullscreen"
						class="w-full h-[500px]"
					/>
				</div>
			</div>
		</section>
	</main>
</template>
