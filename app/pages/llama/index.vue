<template>
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
