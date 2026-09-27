<template>
	<h1 class="pounce-brand">🦊pounce</h1>
</template>

<script setup>
defineProps({
	animate: {
		type: Boolean,
		default: false,
	},
})
</script>

<style lang="scss" scoped>
.pounce-brand {
	font-weight: 500;
	font-size: 25px;
	color: white;
}
.animate {
	.ring {
		transform-origin: center;
		transform-box: fill-box;
		animation-fill-mode: forwards;
		transition: transform 2s ease-in-out;
		&--large {
			animation: spin 1s ease-in-out infinite forwards;
		}
		&--small {
			animation: spin 2s ease-in-out infinite reverse;
		}
	}
	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}
}
</style>
