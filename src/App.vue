<template>
	<div id="app" class="flex-column start pd-16">
		<Alert
			v-for="(alert, index) in alerts"
			:key="`${alert.icon}-${index}`"
			:name="alert.name"
			:icon="alert.icon"
			:color="alert.color"
			v-on:remove="removeAlert"
		/>
		<ButtonDropdown v-on:add="addAlert" />
	</div>
</template>

<script>
import Alert from './components/Alert.vue';
import ButtonDropdown from './components/ButtonDropdown.vue';

export default {
	name: 'app',

	components: {
		Alert,
		ButtonDropdown
	},

	data() {
		return {
			alerts: []
		}
	},

	methods: {
		addAlert(alert) {
			this.alerts = [...new Set([...this.alerts, alert])];
		},

		removeAlert(name) {
			this.alerts = this.alerts.filter(alert => alert.name !== name);
		}
	}
}
</script>

<style>
	* {
		box-sizing: border-box;
	}

	html, body {
		margin: 0;
		padding: 0;
	}

	.flex {
		display: flex;
	}

	.flex-column {
		display: flex;
		flex-direction: column;
	}

	.start {
		justify-content: flex-start;
	}

	.start-center {
		justify-content: flex-start;
		align-items: center;
	}

	.center {
		justify-content: center;
		align-items: center;
	}

	.between {
		justify-content: space-between;
		align-items: center;
	}

	.w-full {
		width: 100%;
	}

	.button {
		background: #bb0100;
		color: #fff;
		font-size: 1.2rem;
		font-weight: bold;
		border: none;
		border-radius: 4px;
		padding: 10px 24px;
		cursor: pointer;
		transition: transform .15s ease-in;
		outline: none;
	}

	.button:hover {
		transform: scale(1.05);
	}

	.relative {
		position: relative;
	}

	.absolute {
		position: absolute;
	}

	.border {
		border: solid .5px #ddd;
	}

	.pd-16 {
		padding: 16px;
	}

	.pd-8-16 {
		padding: 8px 16px;
	}

	.mrr-16 {
		margin-right: 16px;
	}

	.mrl-16 {
		margin-left: 16px;
	}

	.mrt-16 {
		margin-top: 16px;
	}

	.mrb-8 {
		margin-bottom: 8px;
	}
</style>
