<template>
	<div
		v-if="open"
		class="alert w-full flex between pd-8-16 mrb-8"
		:style="`background: ${color}`">
		<div class="flex center">
			<div
				class="alert__icon flex center mrr-16"
				:style="`color: ${color}`"
				v-html="icon">
			</div>
			<div class="alert__message">{{ name }} alert</div>
		</div>
		<div class="alert__close flex center" @click="close(name)">
			&#x2715;
		</div>
	</div>
</template>

<script>
export default {
	name: 'Alert',

	props: {
		name: String,
		icon: String,
		color: String
	},

	data() {
		return {
			open: true
		}
	},

	methods: {
		close(name) {
			this.open = !this.open;
			this.$emit('remove', name)
		}
	}
}
</script>

<style scoped>
	.alert {
		color: #fff;
		font-size: 1rem;
		font-weight: bold;
		border-radius: 4px 4px 0 0;
	}

	.alert__icon {
		font-size: .7rem;
		background: #fff;
		width: 16px;
		height: 16px;
		border-radius: 16px;
		line-height: 3;
	}

	.alert__close {
		font-family: sans-serif;
		font-size: 1rem;
		font-weight: lighter;
		color: #fff;
		cursor: pointer;
	}
</style>
