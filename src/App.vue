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
	#app {
		width: 100%;
	}
	body {
		background: url('/imgs/action_bg.png') no-repeat;
		background-attachment:fixed;
		background-size: cover;
		width: 100%;
		height: 100%;
		margin: 30px 0 0 0;
	}
</style>
