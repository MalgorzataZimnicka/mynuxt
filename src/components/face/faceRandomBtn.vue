<script setup lang="ts">
const props = defineProps(["list", "title"]);
const emit = defineEmits(["randomChanges", "countChanges"]);

let numberChanges = 0;

function random() {
	numberChanges++;
	emit("randomChanges");
	emit("countChanges", numberChanges);
}
</script>
<template>
	<div>
		<button class="random" @click="random()">
			{{ title }}
		</button>
	</div>
</template>
<style scoped></style>
