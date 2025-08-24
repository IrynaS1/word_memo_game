<script setup>
import Header from './components/Header.vue';
import Button from './components/Button.vue';
import Cards from './components/Cards.vue';
</script>

<template>
	<div class="page-wrapper">
		<Header/>
		<Button>Начать</Button>
		<Cards/>
	</div>
</template>

<style scoped>
	.page-wrapper {
		padding: 0 64px;
	}
</style>
