<script setup lang="ts">
const props = defineProps(["title"]);
</script>
<template>
	<div>
		<p>{{ title }}</p>
		<div class="flex">
			<ButtonHoyaVote :value="1" /><ButtonHoyaVote :value="2" /><ButtonHoyaVote
				:value="3"
			/>
		</div>
	</div>
</template>
<style scoped></style>
