<template>Pounce</template>

<script setup lang="ts">
const loading = useLoading()

const config = useRuntimeConfig()
const flags = useFeatureFlags()

const api = computed(() => {
	if (flags.value.demoMode) return 'prod'

	const apiUrl = config.public.apiBaseUrl
	if (apiUrl.startsWith('https://api.modrinth.com')) {
		return 'prod'
	} else if (apiUrl.startsWith('https://staging-api.modrinth.com')) {
		return 'staging'
	} else if (apiUrl.startsWith('localhost') || apiUrl.startsWith('127.0.0.1')) {
		return 'localhost'
	}
	return 'foreign'
})
</script>

<style lang="scss" scoped>
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
