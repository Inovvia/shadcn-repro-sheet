<script lang="ts">
	import '../app.css';
	import { ModeWatcher } from 'mode-watcher';
	import Menu from 'lucide-svelte/icons/menu';
	import * as Sheet from '$lib/components/ui/sheet/';

	interface Props {
		children?: import('svelte').Snippet;
	}

	let { children }: Props = $props();

	let isSheetOpen = $state(false);
</script>

<ModeWatcher />

<header class="sticky top-0 z-50 flex h-16 items-center gap-4 border-b bg-background px-4 md:px-6">
	<Sheet.Root bind:open={isSheetOpen}>
		<Sheet.Trigger
			onclick={() => {
				isSheetOpen = true;
			}}
		>
			<Menu class="h-5 w-5 shrink-0" />
			<span class="sr-only">Toggle navigation menu</span>
		</Sheet.Trigger>
		<Sheet.Content side="left" trapFocus={false}>
			<nav class="grid gap-6 text-lg font-medium">
				<button
					onclick={() => {
						alert('button 1');
					}}
				>
					Button 1
				</button>
				<button
					onclick={() => {
						alert('button 2');
					}}
				>
					Button 2
				</button>
				<button
					onclick={() => {
						alert('button 3');
					}}
				>
					Button 3
				</button>
			</nav>
		</Sheet.Content>
	</Sheet.Root>
</header>

{@render children?.()}
