<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import KanbanBoard from "./components/KanbanBoard.vue";
import Sidebar from "./components/Sidebar.vue";
import ProjectTitle from "./components/ProjectTitle.vue";
import Nav from "./components/Nav.vue";
</script>

<template>
	<div
		class="
			container
			mx-auto
			overflow-hidden
			border-r border-l border-gray-200
		"
	>
		<Nav />

		<div class="flex">
			<div class="w-1/5">
				<Sidebar />
			</div>

			<div class="w-4/5 p-10">
				<ProjectTitle />
				<KanbanBoard />
			</div>
		</div>
	</div>
</template>
