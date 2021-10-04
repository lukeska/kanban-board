<script setup>
import { ref, computed } from "vue";
import draggable from "vuedraggable";
import Ticket from "./Ticket.vue";
import KanbanBoardControls from "./KanbanBoardControls.vue";

const lanes = ref([
	{
		name: "To Do",
		tickets: [
			{
				title: "We don't have a brig. Meh. Calculon is gonna kill us and it's all everybody else's fault!",
				author: "Philip J. Fry",
				created_at: "16 hours ago",
				level: "Medium Level",
				comments_count: 12,
			},
			{
				title: "This opera's as lousy as it is brilliant! Your lyrics lack subtlety. You can't just have your characters announce how they feel.",
				author: "Turanga Leela",
				created_at: "16 hours ago",
				level: "High Level",
				comments_count: 1,
			},
			{
				title: "Stop it, stop it. It's fine. I will 'destroy' you! I can explain. It's very valuable. ",
				author: "Bender Bending Rodriguez",
				created_at: "16 hours ago",
				level: "Low Level",
				comments_count: 12,
			},
			{
				title: "Hey, whatcha watching? Hey! I'm a porno-dealing monster, what do I care what you think? It must be wonderful.",
				author: "Professor Farnsworth",
				created_at: "16 hours ago",
				level: "Medium Level",
				comments_count: 0,
			},
			{
				title: "A superpowers drug you can just rub onto your skin? You'd think it would be something you'd have to freebase.",
				author: "Amy Wong",
				created_at: "16 hours ago",
				level: "High Level",
				comments_count: 56,
			},
			{
				title: "Robot 1-X, save my friends! And Zoidberg! Perhaps, but perhaps your civilization is merely the sewer of an even greater society above you!",
				author: "Hermes Conrad",
				created_at: "16 hours ago",
				level: "Medium Level",
				comments_count: 10,
			},
			{
				title: "You are the last hope of the universe. Stop! Don't shoot fire stick in space canoe!",
				author: "Dr. John A. Zoidberg",
				created_at: "16 hours ago",
				level: "Low Level",
				comments_count: 3,
			},
		],
	},
	{
		name: "In Progress",
		tickets: [
			{
				title: "You are the last hope of the universe. Stop! Don't shoot fire stick in space canoe!",
				author: "Dr. John A. Zoidberg",
				created_at: "16 hours ago",
				level: "Low Level",
				comments_count: 12,
			},
			{
				title: "A superpowers drug you can just rub onto your skin? You'd think it would be something you'd have to freebase.",
				author: "Amy Wong",
				created_at: "16 hours ago",
				level: "High Level",
				comments_count: 2,
			},
			{
				title: "This opera's as lousy as it is brilliant! Your lyrics lack subtlety. You can't just have your characters announce how they feel.",
				author: "Turanga Leela",
				created_at: "16 hours ago",
				level: "High Level",
				comments_count: 12,
			},
		],
	},
	{
		name: "Done",
		tickets: [
			{
				title: "Stop it, stop it. It's fine. I will 'destroy' you! I can explain. It's very valuable. ",
				author: "Bender Bending Rodriguez",
				created_at: "16 hours ago",
				level: "Low Level",
				comments_count: 12,
			},
			{
				title: "Hey, whatcha watching? Hey! I'm a porno-dealing monster, what do I care what you think? It must be wonderful.",
				author: "Professor Farnsworth",
				created_at: "16 hours ago",
				level: "Medium Level",
				comments_count: 0,
			},
			{
				title: "We don't have a brig. Meh. Calculon is gonna kill us and it's all everybody else's fault!",
				author: "Philip J. Fry",
				created_at: "16 hours ago",
				level: "Medium Level",
				comments_count: 12,
			},
			{
				title: "This opera's as lousy as it is brilliant! Your lyrics lack subtlety. You can't just have your characters announce how they feel.",
				author: "Turanga Leela",
				created_at: "16 hours ago",
				level: "High Level",
				comments_count: 1,
			},
		],
	},
]);

const dragOptions = computed(() => {
	return {
		animation: 200,
		disabled: false,
		ghostClass: "ghost",
	};
});
</script>

<template>
	<KanbanBoardControls />

	<div class="grid grid-cols-3 gap-6">
		<div
			v-for="lane in lanes"
			:key="lane.name"
			class="border border-gray-300 rounded-md bg-gray-50"
		>
			<div
				class="
					bg-white
					border-b border-gray-300
					p-4
					rounded-t-md
					flex
					items-center
					justify-between
				"
			>
				<div class="text-lg font-semibold">
					{{ lane.name }}
				</div>

				<div class="flex items-center space-x-4">
					<button
						v-if="lane.name == 'Done'"
						class="text-blue-500 hover:text-blue-700 font-semibold"
					>
						Clear all
					</button>

					<span
						class="
							block
							py-1
							px-3
							bg-gray-200
							rounded-xl
							text-sm
							font-semibold
						"
					>
						{{ lane.tickets.length }}
					</span>
				</div>
			</div>

			<div class="p-4 h-full">
				<draggable
					class="min-h-full"
					:list="lane.tickets"
					group="tickets"
					itemKey="name"
					v-bind="dragOptions"
				>
					<template #item="{ element }">
						<Ticket :ticket="element" />
					</template>
				</draggable>
			</div>
		</div>
	</div>
</template>
