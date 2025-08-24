<script setup>
import { ref } from 'vue';
import Card from './Card.vue';

const data = ref([
	{
	id:1,
	firstWord: 'word  11',
	secondWord:'слово  11'
	},
	{
	id:2,
	firstWord: 'word  25',
	secondWord:'слово  25'
	},
	{
	id:3,
	firstWord: 'word  36',
	secondWord:'слово  36'
	},
{
	id:4,
	firstWord: 'word  47',
	secondWord:'слово  47'
},
]);
</script>

<template>
	<div class="cards-wrapper">
		<Card v-for="(card, id) in data" :key="id" v-bind="card"/>
	</div>
</template>

<style scoped>
	.cards-wrapper {
		display: flex;
		flex-wrap: wrap;
		justify-content: space-between;
	}
</style>