<script lang="ts">
	import { getContext } from 'svelte';

	const i18n = getContext('i18n');

	export let options = {
		// Advanced
		seed: 0,
		stop: '',
		temperature: '',
		repeat_penalty: '',
		repeat_last_n: '',
		mirostat: '',
		mirostat_eta: '',
		mirostat_tau: '',
		top_k: '',
		top_p: '',
		tfs_z: '',
		num_ctx: '',
		num_predict: ''
	};
</script>

<div class=" space-y-3 text-xs">
	<div>
		<div class=" py-0.5 flex w-full justify-between">
			<div class=" w-20 text-xs font-medium self-center">{$i18n.t('Seed')}</div>
			<div class=" flex-1 self-center">
				<input
					class="w-full rounded-lg py-2 px-4 text-sm dark:text-gray-300 dark:bg-gray-850 outline-none"
					type="number"
					placeholder="Enter Seed"
					bind:value={options.seed}
					autocomplete="off"
					min="0"
				/>
			</div>
		</div>
	</div>

	<div>
		<div class=" py-0.5 flex w-full justify-between">
			<div class=" w-20 text-xs font-medium self-center">{$i18n.t('Stop Sequence')}</div>
			<div class=" flex-1 self-center">
				<input
					class="w-full rounded-lg py-2 px-4 text-sm dark:text-gray-300 dark:bg-gray-850 outline-none"
					type="text"
					placeholder={$i18n.t('Enter stop sequence')}
					bind:value={options.stop}
					autocomplete="off"
				/>
			</div>
		</div>
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Temperature')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.temperature = options.temperature === '' ? 0.8 : '';
				}}
			>
				{#if options.temperature === ''}
					<span class="ml-2 self-center"> {$i18n.t('Default')} </span>
				{:else}
					<span class="ml-2 self-center"> {$i18n.t('Custom')} </span>
				{/if}
			</button>
		</div>

		{#if options.temperature !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="1"
						step="0.05"
						bind:value={options.temperature}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.temperature}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="1"
						step="0.05"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Mirostat')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.mirostat = options.mirostat === '' ? 0 : '';
				}}
			>
				{#if options.mirostat === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.mirostat !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="2"
						step="1"
						bind:value={options.mirostat}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.mirostat}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="2"
						step="1"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Mirostat Eta')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.mirostat_eta = options.mirostat_eta === '' ? 0.1 : '';
				}}
			>
				{#if options.mirostat_eta === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.mirostat_eta !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="1"
						step="0.05"
						bind:value={options.mirostat_eta}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.mirostat_eta}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="1"
						step="0.05"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Mirostat Tau')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.mirostat_tau = options.mirostat_tau === '' ? 5.0 : '';
				}}
			>
				{#if options.mirostat_tau === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Custom')}</span>
				{/if}
			</button>
		</div>

		{#if options.mirostat_tau !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="10"
						step="0.5"
						bind:value={options.mirostat_tau}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.mirostat_tau}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="10"
						step="0.5"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Top K')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.top_k = options.top_k === '' ? 40 : '';
				}}
			>
				{#if options.top_k === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.top_k !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="100"
						step="0.5"
						bind:value={options.top_k}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.top_k}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="100"
						step="0.5"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Top P')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.top_p = options.top_p === '' ? 0.9 : '';
				}}
			>
				{#if options.top_p === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.top_p !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="1"
						step="0.05"
						bind:value={options.top_p}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.top_p}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="1"
						step="0.05"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Repeat Penalty')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.repeat_penalty = options.repeat_penalty === '' ? 1.1 : '';
				}}
			>
				{#if options.repeat_penalty === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.repeat_penalty !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="2"
						step="0.05"
						bind:value={options.repeat_penalty}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.repeat_penalty}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="2"
						step="0.05"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Repeat Last N')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.repeat_last_n = options.repeat_last_n === '' ? 64 : '';
				}}
			>
				{#if options.repeat_last_n === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.repeat_last_n !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="-1"
						max="128"
						step="1"
						bind:value={options.repeat_last_n}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.repeat_last_n}
						type="number"
						class=" bg-transparent text-center w-14"
						min="-1"
						max="128"
						step="1"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Tfs Z')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.tfs_z = options.tfs_z === '' ? 1 : '';
				}}
			>
				{#if options.tfs_z === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.tfs_z !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="0"
						max="2"
						step="0.05"
						bind:value={options.tfs_z}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div>
					<input
						bind:value={options.tfs_z}
						type="number"
						class=" bg-transparent text-center w-14"
						min="0"
						max="2"
						step="0.05"
					/>
				</div>
			</div>
		{/if}
	</div>

	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Context Length')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.num_ctx = options.num_ctx === '' ? 2048 : '';
				}}
			>
				{#if options.num_ctx === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.num_ctx !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="-1"
						max="10240000"
						step="1"
						bind:value={options.num_ctx}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div class="">
					<input
						bind:value={options.num_ctx}
						type="number"
						class=" bg-transparent text-center w-14"
						min="-1"
						step="10"
					/>
				</div>
			</div>
		{/if}
	</div>
	<div class=" py-0.5 w-full justify-between">
		<div class="flex w-full justify-between">
			<div class=" self-center text-xs font-medium">{$i18n.t('Max Tokens')}</div>

			<button
				class="p-1 px-3 text-xs flex rounded transition"
				type="button"
				on:click={() => {
					options.num_predict = options.num_predict === '' ? 128 : '';
				}}
			>
				{#if options.num_predict === ''}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{:else}
					<span class="ml-2 self-center">{$i18n.t('Default')}</span>
				{/if}
			</button>
		</div>

		{#if options.num_predict !== ''}
			<div class="flex mt-0.5 space-x-2">
				<div class=" flex-1">
					<input
						id="steps-range"
						type="range"
						min="-2"
						max="16000"
						step="1"
						bind:value={options.num_predict}
						class="w-full h-2 rounded-lg appearance-none cursor-pointer dark:bg-gray-700"
					/>
				</div>
				<div class="">
					<input
						bind:value={options.num_predict}
						type="number"
						class=" bg-transparent text-center w-14"
						min="-2"
						max="16000"
						step="1"
					/>
				</div>
			</div>
		{/if}
	</div>
</div>
