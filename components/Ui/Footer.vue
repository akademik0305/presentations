<script setup>
//===============================-< imports >-===============================
import Service from "~/service/Service";
import urls from "~/service/urls";
const { locale } = useI18n();
const localePath = useLocalePath();
//===============================-< get contact >-===============================
//> variables
const contact = ref();
//> functions
async function getContact() {
	const res = await Service.get(urls.getContactInfo(), locale.value, null);
	contact.value = res.data;
}

getContact();

watch(locale, () => {
	getContact();
});
</script>
<template>
	<!-- footer -->
	<footer class="footer border-t border-border bg-navbar-bg py-8">
		<div class="container">
			<div class="flex flex-col md:flex-row items-start justify-between gap-6">
				<div class="flex flex-col gap-3 w-full md:w-1/2">
					<NuxtLink :to="localePath('/')" class="block max-w-28">
						<h2 class="text-2xl text-main font-medium">Logo</h2>
					</NuxtLink>
					<p class="font-inter text-gray-600">
						<!-- {{ contact?.description }} -->
						Lorem ipsum dolor sit amet consectetur adipisicing elit. Iste earum
						reiciendis asperiores libero ab itaque eaque eius, repellat ratione
						sunt.
					</p>
				</div>

				<div class="flex flex-col gap-3">
					<h4>{{ $t("contact") }}</h4>
					<div class="flex items-center gap-2">
						<a
							v-if="contact?.instagram_url"
							href="https://www.instagram.com/p/DL99vZpN23v/"
							target="_blank"
						>
							<UIcon
								name="hugeicons:instagram"
								class="text-xl text-gray-500 hover:text-main transition"
							/>
						</a>
						<a v-if="contact?.facebook_url" href="#" target="_blank">
							<UIcon
								name="circum:facebook"
								class="text-xl text-gray-500 hover:text-main transition"
							/>
						</a>
						<a v-if="contact?.telegram_url" href="#" target="_blank">
							<UIcon
								name="hugeicons:telegram"
								class="text-xl text-gray-500 hover:text-main transition"
							/>
						</a>
						<a v-if="contact?.youtube_url" href="#" target="_blank">
							<UIcon
								name="hugeicons:youtube"
								class="text-xl text-gray-500 hover:text-main transition"
							/>
						</a>
					</div>
					<a
						:href="`tel:+998 33 180 10 08`"
						class="text-gray-500 font-inter hover:text-main transition-all"
						>{{ $t("phone") }}: +998 33 180 10 08</a
					>
					<a
						:href="`mailto: email`"
						class="text-gray-500 font-inter hover:text-main transition-all"
						>{{ $t("email") }}: Email</a
					>
					<a
						:href="`https://maps.app.goo.gl/xesCLfjJVR1gFbmcA`"
						target="_blank"
						class="text-gray-500 font-inter hover:text-main transition-all"
						>{{ $t("address") }}: Manzil
					</a>
				</div>
			</div>

			<div
				class="border-t border-t-gray-200 mt-6 pt-6 text-center font-inter text-gray-600 text-sm"
			>
				© {{ new Date().getFullYear() }} .{{ $t("footer_copy") }}
			</div>
			<div class="mt-4 text-center font-inter text-gray-600 text-sm">
				Made with ❤️ by:
				<a
					href="https://t.me/webcode_team"
					target="_blank"
					class="text-blue-400 hover:underline"
					>WebCode</a
				>
				Team
			</div>
		</div>
	</footer>
	<!-- footer -->
</template>
