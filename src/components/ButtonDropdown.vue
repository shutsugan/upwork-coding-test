<template>
	<div class="button-dropdown relative">
		<button
			class="button flex between mrt-16"
			@click="toggleDropdown">
			Alerts
			<div
				class="arrow mrl-16"
				:class="{'up': toggle, 'down': !toggle}">
			</div>
		</button>
		<div
			class="dropdown flex-column center absolute"
			v-show="toggle">
			<div class="arrow up dropdown__arrow absolute"></div>
			<div
				v-for="alert in alerts"
				:key="alert.name"
				class="flex list w-full center pd-16"
				@click="setAlert(alert)">
				{{ alert.name }}
			</div>
		</div>
	</div>
</template>

<script>
export default {
	name: 'Alert',

	data() {
		return {
			toggle: false,
			alerts: [
				{
					name: 'success',
					icon: '&#10003;',
					color: '#2c8000'
				},
				{
					name: 'error',
					icon: '&#x2715;',
					color: '#880000'
				},
				{
					name: 'warning',
					icon: '!',
					color: '#f16600'
				},
				{
					name: 'info',
					icon: '<em>i</em>',
					color: '#2b00ff'
				}
			]
		}
	},

	methods: {
		toggleDropdown() {
			this.toggle = !this.toggle;
		},

		setAlert(alert) {
			this.toggleDropdown();
			this.$emit('add', alert);
		}
	}
}
</script>

<style scoped>
	.arrow {
		width: 0; 
		height: 0; 
		border-left: 6px solid transparent;
		border-right: 6px solid transparent;
	}

	.up {
		border-bottom: 6px solid #fff;
	}

	.down {
		border-top: 6px solid #fff;
	}

	.dropdown {
		width: 130px;
    	border: solid .5px #ddd;
		box-shadow: 0 1px 3px rgba(0,0,0,0.12), 0 1px 2px rgba(0,0,0,0.24);
	}

	.dropdown__arrow {
		top: -6px;
	}

	.list {
		text-transform: capitalize;
		font-size: 1.1rem;
		font-weight: bold;
		color: #929395;
		cursor: pointer;
		transition: all .15s ease-in;
	}

	.list:hover {
		background: #ddd;
		color: #000;
	}
</style>
