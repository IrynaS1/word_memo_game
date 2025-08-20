<script setup>
import Button from './Button.vue';
import CloseIcon from '../icons/CloseIcon.vue';
import TickIcon from '../icons/TickIcon.vue';

const flipCard = () => {

};
</script>

<template>
	<div class="card">
		<div class="card__content-wrapper">
			<div class="card__content-wrapper-els card__number">01</div>
		<Button 
			class="card__content-wrapper-els card__actions" 
			@click="flipCard"
			>
			Перевернуть
		</Button> 
			<!-- <Button 
			class="card__content-wrapper-els card__actions card__btns" 
			@click="flipCard"
			>
			<CloseIcon/>
			<TickIcon/>
		</Button> -->
		<div class="card__content">unadmitted</div>
		</div>
	</div>
</template>

<style scoped>
	.card {
		width: 250px;
		height: 376px;
		padding: 19px 28px;
		border-radius: 16px;
		box-shadow: 0px 0px 16px 0px rgba(0, 0, 0, 0.1);
		background-color: var(--color-secondary);
	}

	.card:hover {
		box-shadow: 10px 10px 10px 0px rgba(0, 0, 0, 0.05);
	}

	.card__content-wrapper {		
		display: flex;
		align-items: center;
		justify-content: center;
		position: relative;
		width: 100%;
		height: 100%;
		border: 1px solid var(--bg-color);
		border-radius: 12px;
	}

	.card__content-wrapper-els {
 		position: absolute; 
		background-color: var(--color-secondary);
	}

	.card__number {
		padding: 0 2px;
		left: 16px;
		top: -10px;
		color: var(--color--text-content);
		font-size: 14px;
		font-weight: 400;
	}

	.card__actions {
		left: 30%;
		bottom: -10px;
		padding: 0 4px;
		color: rgba(34, 34, 34, 1);
		font-family: var(--font);
		font-size: 12px;
		font-weight: 600;
		line-height: 18px;
		border: none;
		text-transform: uppercase;
	}

	.card__btns {
		display: flex;
		padding: 0 9px;
		gap: 32px;
	}
</style>