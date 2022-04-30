<script context="module">
	import { browser, dev } from '$app/env';

	// we don't need any JS on this page, though we'll load
	// it in dev so that we get hot module replacement...
	export const hydrate = dev;

	// ...but if the client-side router is already loaded
	// (i.e. we came here from elsewhere in the app), use it
	export const router = browser;

	// since there's no dynamic data here, we can prerender
	// it so that it gets served as a static asset in prod
	export const prerender = true;
</script>

<svelte:head>
	<title>About</title>
	<meta name="description" content="About this app" />
</svelte:head>

<div class="content">
	<h1>About this app</h1>

	<p>
		This is a <a href="https://kit.svelte.dev">SvelteKit</a> app template by
		<a href="https://aidantilgner.dev" target="_blank">Aidan Tilgner</a>. You can make it your own
		by running the following commands:
	</p>
	<pre><code>npm install</code></pre>
	<pre><code
			>npm run dev <span style="cursor:pointer;font-weight: 600;" title="These flags are optional"
				>-- --open</span
			></code
		></pre>

	<p>
		This template is a standard SvelteKit app with the addition of the following libraries and
		dependencies:
	</p>
	<ul>
		<li>
			<pre style="display:inline;">Sass</pre>
			: A preprocessing library that converts
			<pre style="display:inline;">.scss/.sass</pre>
			files to css at buildtime.
		</li>
	</ul>
</div>

<style>
	.content {
		width: 100%;
		max-width: var(--column-width);
		margin: var(--column-margin-top) auto 0 auto;
	}
</style>
