<template>
	<div id="app">
		<card></card>
	</div>
</template>

<script>
	import card from './components/card.vue';

	export default {
		name: 'app',
		components: {
			card
		},
	}
</script>

<style>
	body {
		background: url('/imgs/action_bg.png') no-repeat;
		background-attachment:fixed;
		background-size: cover;
		width: 100%;
		height: 100%;
		margin: 0;
		margin-top: 30px;
	}
</style>
