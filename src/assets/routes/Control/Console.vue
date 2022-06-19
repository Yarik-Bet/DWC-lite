<template>
<v-row>
	<v-col order="0" order-md="1" cols="12" sm="12" md="12" xl="12">
		<v-row :dense="$vuetify.breakpoint.mobile">
			<v-col cols="8" order="0">
				<fff-dashboard-panel></fff-dashboard-panel>
			</v-col>
			<v-col cols="4" order="1">
				<macro-file-list></macro-file-list>
			</v-col>
			<!--<v-col cols="4" class="pt-1" order="2">
				<code-input solo></code-input>
				<event-list></event-list>
			</v-col>
		
		v-col cols="6" order="2">
			<event-list></event-list>
		</v-col-->
		
		</v-row>
	</v-col>
		<v-col order="1" order-md="1" cols="12" sm="12" md="12" xl="12">
		<v-row :dense="$vuetify.breakpoint.mobile">
			<!--<v-col cols="8" order="0">
				<fff-dashboard-panel></fff-dashboard-panel>
			</v-col>
			<v-col cols="4" order="1">
				<macro-file-list></macro-file-list>
			</v-col>-->
			<v-col cols="12" class="pt-1" order="2">
				<code-input solo></code-input>
				<event-list></event-list>
			</v-col>
		
		<!--v-col cols="6" order="2">
			<event-list></event-list>
		</v-col-->
		
		</v-row>
	</v-col>
	</v-row>
</template>
<!--template>
	<div class="mb-3">
		<fff-dashboard-panel></fff-dashboard-panel>
	</div>
</template-->
<script>
'use strict'

import { mapMutations } from 'vuex'

import { registerRoute } from '..'

export default {
	install() {
		// Register a route via Control -> Console
		registerRoute(this, {
			Control: {
				Console: {
					icon: 'mdi-code-tags',
					caption: 'menu.control.console',
					path: '/Console'
				}
			}
		});
	},
	methods: mapMutations(['hideCodeReplyNotifications', 'showCodeReplyNotifications']),
	activated() {
		this.hideCodeReplyNotifications();
	},
	deactivated() {
		this.showCodeReplyNotifications();
	}
}
</script>
