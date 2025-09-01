<script setup>
import BoldHeart from '../icons/BoldHeart.vue';

const { score } = defineProps({
	score: Number,
}); 
</script>

<template>
		<div class="header-score">
			<span>{{ score }}</span>
			<BoldHeart/>
		</div>
</template>

<style scoped>
	.header-score {
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 10px;
		padding: 12px 24px;
		border-radius: 36px;
		box-shadow: 0px 0px 4px 0px rgba(0, 0, 0, 0.15);
		background: rgba(204, 232, 255, 1);
	}
</style>