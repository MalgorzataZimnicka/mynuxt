<script setup lang="ts">
import { Ref } from "vue";
type Props = { newColorOptions: string[]; drawnColors: string[] };
const props = defineProps<Props>();

const pickedColorsByUser: Ref<string[]> = ref([]);

function setColor(color: string) {
	pickedColorsByUser.value.push(color);
}
</script>
<template>
	<div class="w-86 h-20 border-2 border-stone-700 flex items-center">
		<GameColorPickBtn
			v-for="option in newColorOptions"
			:newColorOptions="newColorOptions"
			@pickedColor="setColor"
		/>
		<GameColorCheck
			class="mr-0 m-auto"
			:drawnColors="drawnColors"
			:newColorOptions="newColorOptions"
		/>
	</div>
</template>
<style scoped></style>
