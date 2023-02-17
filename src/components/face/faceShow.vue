<script setup lang="ts">
const props = defineProps([
	"PickedFaceColor",
	"PickedEyebrow",
	"PickedEye",
	"PickedLips",
]);
</script>
<template>
	<div
		class="flex flex-col items-center w-64 h-64 rounded-full border-2 border-stone-700"
		:class="PickedFaceColor"
	>
		<div class="w-32 flex justify-between mt-12">
			<div :class="PickedEyebrow"></div>
			<div class="mirror"><div :class="PickedEyebrow"></div></div>
		</div>
		<div class="w-24 flex justify-item-between mt-24">
			<div :class="PickedEye"></div>
			<div class="mirror ml-24">
				<div :class="PickedEye"></div>
			</div>
		</div>
		<div class="mt-40" :class="PickedLips"></div>
	</div>
</template>
<style scoped></style>
