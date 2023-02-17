<script setup lang="ts">
import { Ref } from "vue";
type Emits = {
	(eventName: "pickedColor", color: string): void;
};
const emit = defineEmits<Emits>();
type Props = { newColorOptions: string[] };
const props = defineProps<Props>();

const visibleOption: Ref<boolean> = ref(false);

const pickedColor: Ref<string> = ref("");

function pickedColorFunction(color: string) {
	pickedColor.value = color;
	emit("pickedColor", color);
}
</script>
<template>
	<div>
		<div
			class="w-8 h-8 rounded-full border-2 border-stone-700"
			@click="(visibleOption = !visibleOption), clg"
			:class="pickedColor"
		>
			<div
				class="w-4 h-4 rounded-full border-2 ml-8 border-stone-700"
				v-if="visibleOption"
				v-for="color in newColorOptions"
				:class="color"
				@click="pickedColorFunction(color), visibleOption != visibleOption"
			></div>
		</div>
	</div>
</template>
<style scoped></style>
