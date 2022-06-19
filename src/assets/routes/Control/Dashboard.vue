<style scoped>
.chart-height-limit {
	max-height: 320px;
}
</style>

<template>
	<div class="d-flex flex-column">
		<job-progress></job-progress>

		<v-row class="mt-0" :dense="$vuetify.breakpoint.mobile">
			<v-col order="0" order-md="1" cols="12" sm="6" md="3" xl="3">
				<v-row align="center" :dense="$vuetify.breakpoint.mobile">
					<v-col cols="12">
						<job-control-panel></job-control-panel>
					</v-col>
					<!--v-col class="hidden-sm-and-down">
						<job-info-panel></job-info-panel>
					</v-col-->
					<v-col cols="12">
						<fans-panel></fans-panel>
					</v-col>
					<v-col cols="12">
						<speed-factor-panel></speed-factor-panel>
					</v-col>
					<v-col cols="12">
						<extrusion-factors-panel></extrusion-factors-panel>
					</v-col>

				</v-row>
			</v-col>

			<v-col order="3" order-md="13" cols="12" md="9" xl="9">
			<!--layer-chart class="chart-height-limit mb-5"></layer-chart-->

				<v-row class="d-flex flex-row"> <!--было flex-grow-0 flex-shrink-1 d-none d-md-flex-->
				
					<!--<v-col cols="12">
						<job-estimations-panel></job-estimations-panel>
					</v-col>
					v-col cols="12">
						<job-data-panel></job-data-panel>
					</v-col-->
					<v-col cols="9">
					<job-file-list></job-file-list>
					</v-col>

					<v-col cols="3">
					<macro-list></macro-list>
					</v-col>
				</v-row>

				<!--<v-row class="flex-grow-0 flex-shrink-1 hidden-sm-and-up mt-3">
					<v-col cols="6" md="6">
						<fans-panel></fans-panel>
					</v-col>
					<v-col cols="6" md="6">
						<speed-factor-panel></speed-factor-panel>
					</v-col>
				</v-row>-->
			</v-col>

			<!--<v-col order="0" order-md="3" cols="12" sm="6" md="4" xl="3">
				<v-row :dense="$vuetify.breakpoint.mobile">
					<v-col cols="12" class="hidden-md-and-up">
						<job-estimations-panel></job-estimations-panel>
					</v-col>
					<v-col cols="12" class="hidden-md-and-up">
						<job-data-panel></job-data-panel>
					</v-col>
					v-col cols="12" class="hidden-md-and-up">
						<job-info-panel></job-info-panel>
					</v-col

					<v-col cols="12" class="hidden-sm-only">
						<speed-factor-panel></speed-factor-panel>
					</v-col>
					<v-col cols="12">
						<fans-panel></fans-panel>
					</v-col>
					<v-col cols="12" class="hidden-sm-only">
						<extrusion-factors-panel></extrusion-factors-panel>
					</v-col>
					
				</v-row>
			</v-col>-->
		</v-row>
		<!--<v-row>
		<v-col cols="12" class="d-flex justify-content-end">
			<job-file-list></job-file-list>
		</v-col>
	</v-row>-->
	</div>
	
</template>

<!--<template>
	<div class="mb-3">
		<fff-dashboard-panel v-if="isFFForUnset"></fff-dashboard-panel>
		<cnc-dashboard-panel v-else></cnc-dashboard-panel>
	</div>
</template>-->

<script>
'use strict';

import { mapState } from 'vuex';

import { registerRoute } from '..'
import { DashboardMode } from '../../store/settings.js'
import { MachineMode } from '../../store/machine/modelEnums.js'

export default {
    install() {
        // Register a route via Control -> Dashboard
        registerRoute(this, {
            Control: {
                Dashboard: {
                    icon: 'mdi-view-dashboard',
                    caption: 'menu.control.dashboard',
                    path: '/'
                }
            }
        });
    },

	computed: {
		...mapState('machine/model', {
			atxPower: state => state.state.atxPower,
			machineMode: state => state.state.machineMode
		}),
		...mapState('settings', ['dashboardMode']),
		isFFForUnset() {
			if (this.dashboardMode === DashboardMode.default) {
				return !this.machineMode || this.machineMode === MachineMode.fff;
			}
			return this.dashboardMode === DashboardMode.fff;
		},
	},
};
</script>


