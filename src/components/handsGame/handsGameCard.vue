<script setup lang="ts">
type Option = {
	name: string;
	src: string;
	isActive: boolean;
};
const props = defineProps<{
	option: Option;
}>();

const emit = defineEmits<{
	(eventName: "playerChoice", name: string, isActive: boolean): void;
}>();

const activeCard = ref("active-card");
function playerSelected(name: string, isActive: boolean) {
	emit("playerChoice", name, isActive);
}
</script>
<template>
	<div class="w-full hands" :class="[props.option.isActive ? activeCard : '']">
		<div>{{ option.src }}</div>
		<img
			class="w-1/2 p-4 rounded"
			:src="option.src"
			alt="card with hand"
			:nameHand="option.name"
			@click="playerSelected(option.name, option.isActive)"
		/>
	</div>
</template>
<style scoped></style>
