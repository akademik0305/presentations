<script lang="ts" setup>
//===============================-< imports >-===============================
// types
// import type { TRestaurant, TRestaurantsData } from '~/types/api.types'
// // service
import Service from "~/service/Service";
import urls from "~/service/urls";

// //> utils
const { locale } = useI18n();
const token = useToken();
const localePath = useLocalePath();
// const router = useRouter()
// const localePath = useLocalePath()

//===============================-< categories >-===============================
// //> variables
// const categoriesRef = ref(null)
// const categoriesSwiper = useSwiper(categoriesRef, {
// 	slidesPerView: 6,
// 	spaceBetween: 20,
// })
//> functions

//===============================-< get  banner >-===============================
//> variables
const banners = ref();
//> functions
async function getBanners() {
	const res = await Service.get(urls.getBanners(), locale.value, null);

	banners.value = res.data;
}

getBanners();

//===============================-< banners swiper >-===============================
//> variables
const bannersRef = ref(null);
const bannersSwiper = useSwiper(bannersRef, {
	spaceBetween: 20,
	loop: true,
	speed: 500,
	autoplay: {
		delay: 2000,
		disableOnInteraction: false,
	},
	pagination: {
		clickable: true,
	},
});
//> functions
</script>
<template>
	<main class="">
		<!-- banner -->
		<header class="pb-10">
			<div class="container">
				<ClientOnly>
					<div class="relative">
						<swiper-container
							ref="bannersRef"
							:init="true"
							class="overflow-hidden"
						>
							<swiper-slide class="h-[40svh] md:max-h-[500px]">
								<img
									class="w-full h-full object-cover"
									src="~/assets/images/jpg/banner-1.jpeg"
									alt="kfc"
								/>
							</swiper-slide>
							<swiper-slide class="h-[40svh] md:max-h-[500px]">
								<img
									class="w-full h-full object-cover"
									src="~/assets/images/jpg/banner-2.jpeg"
									alt="kfc"
								/>
							</swiper-slide>
							<swiper-slide class="h-[40svh] md:max-h-[500px]">
								<img
									class="w-full h-full object-cover"
									src="~/assets/images/jpg/banner-3.jpeg"
									alt="kfc"
								/>
							</swiper-slide>
						</swiper-container>
						<button
							class="absolute top-1/2 -translate-y-1/2 left-0 w-15 h-[40svh] md:h-[500px] bg-gradient-to-r from-white/40 to-transparent hidden md:flex items-center justify-center p-0 z-10"
							@click="bannersSwiper.prev()"
						>
							<UIcon name="tabler:chevron-left" class="text-2xl text-main" />
						</button>
						<button
							class="absolute top-1/2 -translate-y-1/2 right-0 w-15 h-[40svh] md:h-[500px] bg-gradient-to-r from-transparent to-white/40 hidden md:flex items-center justify-center p-0 z-10"
							@click="bannersSwiper.next()"
						>
							<UIcon name="tabler:chevron-right" class="text-2xl text-main" />
						</button>
					</div>
				</ClientOnly>
			</div>
		</header>
		<!-- banner -->
	</main>
</template>
