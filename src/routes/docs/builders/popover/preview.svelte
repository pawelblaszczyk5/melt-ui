<script lang="ts">
	import { createPopover } from '$lib';
	import { Docs } from '$routes/(components)';
	import { fade } from 'svelte/transition';
	import Settings2 from '~icons/lucide/settings2';

	const { trigger, content, open, arrow } = createPopover();
</script>

<Docs.PreviewWrapper>
	<button type="button" class="trigger" {...$trigger()} aria-label="Update dimensions">
		<Settings2 class="h-4 w-4" />
		<span class="sr-only">Open Popover</span>
	</button>

	{#if $open}
		<div {...$content} transition:fade|local={{ duration: 100 }} class="content">
			<div {...$arrow} />
			<div class="flex flex-col gap-2.5">
				<p>Dimensions</p>
				<fieldset>
					<label for="width"> Width </label>
					<input id="width" value="100%" class="input" />
				</fieldset>
				<fieldset>
					<label for="maxWidth"> Max. width </label>
					<input id="maxWidth" value="300px" class="input" />
				</fieldset>
				<fieldset>
					<label for="height"> Height </label>
					<input id="height" value="25px" class="input" />
				</fieldset>
				<fieldset>
					<label for="maxHeight"> Max. height </label>
					<input id="maxHeight" class="input" />
				</fieldset>
			</div>
		</div>
	{/if}
</Docs.PreviewWrapper>

<style lang="postcss">
	fieldset {
		@apply flex items-center gap-5;
	}

	label {
		@apply w-[75px] text-sm text-magnum-700;
	}

	p {
		@apply mb-2 font-medium text-neutral-900;
	}

	.input {
		@apply flex h-8 w-full rounded-md border border-magnum-800 bg-transparent px-2.5 text-sm;
		@apply ring-offset-magnum-300 focus-visible:outline-none focus-visible:ring;
		@apply focus-visible:ring-magnum-400 focus-visible:ring-offset-1;
		@apply flex-1 items-center justify-center;
		@apply px-2.5 text-sm leading-none text-magnum-700;
	}

	.trigger {
		@apply inline-flex h-9 w-9 items-center justify-center rounded-full bg-white p-0 text-sm font-medium;
		@apply text-magnum-900 transition-colors hover:bg-white/90 focus-visible:outline-none;
		@apply focus-visible:ring focus-visible:ring-magnum-400 focus-visible:ring-offset-2;
	}

	.content {
		@apply z-10 w-60 rounded-[4px] bg-white p-5 shadow-sm;
	}
</style>
