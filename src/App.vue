<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import KanbanBoard from "./components/KanbanBoard.vue";
import Sidebar from "./components/Sidebar.vue";
import ProjectTitle from "./components/ProjectTitle.vue";
import Nav from "./components/Nav.vue";
</script>

<template>
	<div>
		<Nav />
		<Sidebar />
		<ProjectTitle />
		<KanbanBoard />
	</div>
</template>
