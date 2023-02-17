<script setup lang="ts">
import { Ref } from "vue";
const props = defineProps(["list", "title"]);
const emit = defineEmits(["property", "countChanges"]);

const showList = ref(false);

let numberChanges = 0;

function changeProperty(item: string) {
	numberChanges++;
	showList.value = false;
	emit("countChanges", numberChanges);
	emit("property", item);
}
</script>
<template>
	<div>
		<button @click="showList = !showList" class="drop-shadow-md">
			{{ title }}
		</button>
		<TransitionGroup
			><div v-if="showList === true" class="absolute">
				<button
					@click="changeProperty(item)"
					v-for="item of list"
					class="drop-shadow-md"
				>
					<div :class="item" class="flex scale-50"></div>
				</button></div
		></TransitionGroup>
	</div>
</template>
<style scoped>
.v-enter-active,
.v-leave-active {
	transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
	opacity: 0;
}
</style>
