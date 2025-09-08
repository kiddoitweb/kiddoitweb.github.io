<template>
    <div class="space-y-4">
        <div
            class="space-y-4 relative border border-gray-300 ring-4 ring-gray-50 rounded-lg overflow-hidden"
        >
            <div class="w-full">
                <img class="w-full" src="/llama.jpeg" alt="Llama" />
            </div>
            <!-- <hr class="my-4" /> -->

            <div
                class="absolute flex justify-between px-4 align-middle bottom-0 left-0 backdrop-blur-sm w-full border-t border-gray-50/20"
            >
                <div class="pt-1">
                    <div class="font-bold leading-7">دوستی با رافی</div>
                    <div class="text-sm">راحتتر بشنوید و لذت ببرید</div>
                </div>
                <audio class="hidden" ref="audioElement" :src="audioSrc"></audio>
                <button
                    @click="togglePlay"
                    type="button"
                    class="cursor-pointer bg-white/90 text-slate-900 dark:bg-slate-100 dark:text-slate-700 flex-none -my-2 w-20 h-20 rounded-full ring-1 ring-slate-900/5 shadow-md flex items-center justify-center"
                    aria-label="Pause"
                >
                    <UIcon
                        v-if="!isPlaying"
                        name="solar:play-bold-duotone"
                        size="28"
                    />
                    <UIcon
                        v-if="isPlaying"
                        name="solar:pause-bold-duotone"
                        size="28"
                    />
                </button>
            </div>
        </div>
        <div class="grid grid-cols-1 sm:grid-cols-2 p-4 bg-gray-50 relative border border-gray-300 ring-4 ring-gray-50 rounded-lg overflow-hidden">
            <div>
                <h3 class="font-bold leading-9">محتوای درون پکیج</h3>
                <ul class="leading-7">
                    <li class="flex align-middle items-center"><UIcon name="solar:alt-arrow-left-bold-duotone" size="20"/> کتاب</li>
                    <li class="flex align-middle items-center"><UIcon name="solar:alt-arrow-left-bold-duotone" size="20"/> بازی سودوکو مربوط به کتاب</li>
                    <li class="flex align-middle items-center"><UIcon name="solar:alt-arrow-left-bold-duotone" size="20"/> شش فلش کارت آموزشی انگلیسی</li>
                    <li class="flex align-middle items-center"><UIcon name="solar:alt-arrow-left-bold-duotone" size="20"/> برچست شخصیت‌های کتاب</li>
                    <li class="flex align-middle items-center"><UIcon name="solar:alt-arrow-left-bold-duotone" size="20"/> فایل صوتی فارسی کتاب</li>
                </ul>
            </div>
            <div class="text-center sm:pt-18">
                <div class="relative inline-flex  group items-center justify-center">
                    <div
                        class="absolute transitiona-all duration-1000 opacity-70 -inset-px bg-gradient-to-r from-[#44BCFF] via-[#FF44EC] to-[#FF675E] rounded-xl blur-lg group-hover:opacity-100 group-hover:-inset-1 group-hover:duration-200 animate-tilt">
                    </div>
                    <a href="tel:1234567890" title="خرید پکیج"
                        class="relative inline-flex items-center justify-center font-light px-6 py-2 text-md text-white transition-all duration-200 bg-gradient-to-br from-red-700 to-orange-600 rounded-md"
                        role="button">خرید پکیج
                    </a>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref } from "vue";

const audioElement = ref<HTMLAudioElement>();
const isPlaying = ref(false);
const audioSrc = "/llama.mp3";

const togglePlay = () => {
    if (!audioElement.value) return;

    if (isPlaying.value) {
        audioElement.value.pause();
    } else {
        audioElement.value.play();
    }
    isPlaying.value = !isPlaying.value;
};
</script>
