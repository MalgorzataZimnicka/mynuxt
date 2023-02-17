<script setup lang="ts">
import { Ref } from "vue";
const emit = defineEmits(["increaseNumber"]);
const props = defineProps<{ levelName: string }>();
const number: Ref<number> = ref(0);

function increaseNumber() {
	number.value++;
	emit("increaseNumber", number.value);
}
</script>
<template>
	<div>
		<button @click="increaseNumber">{{ levelName }}</button>
	</div>
</template>
<style scoped></style>
