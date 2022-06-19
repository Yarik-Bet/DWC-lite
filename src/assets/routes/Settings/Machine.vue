<template>
	<v-row>
		<v-col>
			<system-file-list></system-file-list>
		</v-col>
	</v-row>
</template>

<script>
'use strict'

import { registerRoute } from '..'

export default {
	install() {
		// Register a route via Settings -> Machine
		registerRoute(this, {
			Settings: {
				Machine: {
					icon: 'mdi-cogs',
					caption: 'menu.settings.machine',
					path: '/Settings/Machine'
				}
			}
		});
	}
}
</script>
