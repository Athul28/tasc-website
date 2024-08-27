<script lang="ts">
	import type EventData from '../types/EventData';
	import * as Accordion from '$lib/components/ui/accordion';

	const options: Intl.DateTimeFormatOptions = {
		day: 'numeric',
		month: 'long',
		year: 'numeric'
	};

	export let events: EventData[];
	let years = ['January', 'February', 'March', 'April', 'May', 'June'];
	let includedMonths = [1, 2, 3, 4, 5, 6];
</script>

<div class="mx-20 my-20">
	<Accordion.Root>
		<Accordion.Item value="item-1">
			<Accordion.Trigger>2023-24</Accordion.Trigger>
			<Accordion.Content
				><div class={`grid-container mx-20 gap-10 py-16 `}>
					{#each events as event}
						{#if event.date && ((event.date.toDate().getFullYear() == '2023' && !includedMonths.includes(event.date.toDate().getMonth())) || (event.date.toDate().getFullYear() == '2024' && includedMonths.includes(event.data.toDate().getMonth())))}
							<div class="flex w-full flex-col">
								<div class="dark:custom-shadow-black bg-muted-light dark:bg-muted-dark flex-1 rounded-lg px-5 py-8 shadow-xl dark:drop-shadow-md">
									<div class="flex justify-center">
										{#if event.image}
											<img src={event?.image} alt={event.title} class="border-muted-light dark:border-muted-dark border object-cover" />
										{/if}
									</div>
									<h1 class="py-4 text-center text-2xl font-bold">{event.title}</h1>
									{#if event.date}
										<h2 class="text-center text-xl">Date: {event.date.toDate().toLocaleDateString(undefined, options)}</h2>
									{/if}
									{#if event.time}
										<h2 class="text-center text-xl">Time: {event.time}</h2>
									{/if}
									{#if event.venue}
										<h2 class="text-center text-xl">Venue: {event?.venue}</h2>
									{/if}

									<div class="flex items-center justify-center pt-4">
										{#if event.registrationLink}
											<a href={event.registrationLink} target="_blank">
												<button class="bg-brand rounded-xl px-4 py-2 text-white duration-200 hover:scale-110"> Register Now </button>
											</a>
										{/if}
										<!-- <button class="rounded-xl bg-brand px-4 py-2 text-white">Registration Closed! Spot Registrations are Available</button> -->
									</div>
								</div>
							</div>
						{/if}
					{/each}
				</div></Accordion.Content
			>
		</Accordion.Item>
		<Accordion.Item value="item-2">
			<Accordion.Trigger>2022-23</Accordion.Trigger>
			<Accordion.Content
				><div class={`grid-container mx-20 gap-10 py-16 `}>
					{#each events as event}
						{#if event.date && ((event.date.toDate().getFullYear() == '2022' && !includedMonths.includes(event.date.toDate().getMonth())) || (event.date.toDate().getFullYear() == '2023' && includedMonths.includes(event.date.toDate().getMonth())))}
							<div class="flex w-full flex-col">
								<div class="dark:custom-shadow-black bg-muted-light dark:bg-muted-dark flex-1 rounded-lg px-5 py-8 shadow-xl dark:drop-shadow-md">
									<div class="flex justify-center">
										{#if event.image}
											<img src={event?.image} alt={event.title} class="border-muted-light dark:border-muted-dark border object-cover" />
										{/if}
									</div>
									<h1 class="py-4 text-center text-2xl font-bold">{event.title}</h1>
									{#if event.date}
										<h2 class="text-center text-xl">Date: {event.date.toDate().toLocaleDateString(undefined, options)}</h2>
									{/if}
									{#if event.time}
										<h2 class="text-center text-xl">Time: {event.time}</h2>
									{/if}
									{#if event.venue}
										<h2 class="text-center text-xl">Venue: {event?.venue}</h2>
									{/if}

									<div class="flex items-center justify-center pt-4">
										{#if event.registrationLink}
											<a href={event.registrationLink} target="_blank">
												<button class="bg-brand rounded-xl px-4 py-2 text-white duration-200 hover:scale-110"> Register Now </button>
											</a>
										{/if}
										<!-- <button class="rounded-xl bg-brand px-4 py-2 text-white">Registration Closed! Spot Registrations are Available</button> -->
									</div>
								</div>
							</div>
						{/if}
					{/each}
				</div></Accordion.Content
			>
		</Accordion.Item>
	</Accordion.Root>
</div>

<!-- <div class={`grid-container mx-20 gap-10 py-16 `}>
	{#each events as event}
		<div class="flex w-full flex-col">
			<div class="dark:custom-shadow-black bg-muted-light dark:bg-muted-dark flex-1 rounded-lg px-5 py-8 shadow-xl dark:drop-shadow-md">
				<div class="flex justify-center">
					{#if event.image}
						<img src={event?.image} alt={event.title} class="border-muted-light dark:border-muted-dark border object-cover" />
					{/if}
				</div>
				<h1 class="py-4 text-center text-2xl font-bold">{event.title}</h1>
				{#if event.date}
					<h2 class="text-center text-xl">Date: {event.date.toDate().toLocaleDateString(undefined, options)}</h2>
				{/if}
				{#if event.time}
					<h2 class="text-center text-xl">Time: {event.time}</h2>
				{/if}
				{#if event.venue}
					<h2 class="text-center text-xl">Venue: {event?.venue}</h2>
				{/if}

				<div class="flex items-center justify-center pt-4">
					{#if event.registrationLink}
						<a href={event.registrationLink} target="_blank">
							<button class="bg-brand rounded-xl px-4 py-2 text-white duration-200 hover:scale-110"> Register Now </button>
						</a>
					{/if}
					<button class="rounded-xl bg-brand px-4 py-2 text-white">Registration Closed! Spot Registrations are Available</button>#this was a comment
				</div>
			</div>
		</div>
	{/each}
</div> -->

<style>
	.grid-container {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(18rem, 1fr));
		justify-items: center;
		justify-content: end;
		align-content: end;
		row-gap: 4rem;
	}
</style>
