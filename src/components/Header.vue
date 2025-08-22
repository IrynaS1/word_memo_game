<script setup>
import Score from './Score.vue';

</script>

<template>
	<div class="header">
		<h1 class="main-title">Запомни слово</h1>
		<Score/>
	</div>
</template>

<style scoped>
	.header {
		display:flex;
		align-items: center;
		justify-content: space-between;
		padding: 36px 64px;
	}

	.main-title {
		color: var(--color-primary);
		font-family: Roboto;
		font-size: 16px;
		font-weight: 600;
		line-height: 24px;
		letter-spacing: 12%;
		text-transform: uppercase;
	}
</style>