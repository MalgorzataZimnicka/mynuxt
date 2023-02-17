<script setup lang="ts">
import { Ref } from "vue";
type Props = { newColorOptions: string[]; drawnColors: string[] };
const props = defineProps<Props>();

const visible: Ref<boolean> = ref(true);

function checkColor() {}
</script>
<template>
	<div>
		<div class="w-20 h-20 flex items-center justify-around">
			<button v-if="visible" @click="checkColor, (visible = !visible)">
				Check
			</button>
			<div class="flex">
				<div
					v-if="visible === false"
					v-for="colors in drawnColors"
					class="w-3 h-3 rounded-full border-2 border-stone-700 m-1"
				></div>
			</div>
		</div>
	</div>
</template>
<style scoped></style>
