<script>
	import { page } from '$app/stores';

	let menuOpen = false;
	let pg;

	page.subscribe((page) => {
		pg = page;
	});
</script>

<header class="header">
	<p class="title">Dane's Site</p>
	{#if !menuOpen}
		<i
			class="material-icons menubar"
			on:click={(e) => {
				menuOpen = true;
			}}>menu</i
		>
	{/if}
	<div class="nav-items" />
	{#if menuOpen}
		<div class="nav-overlay">
			<i
				class="material-icons closeicon"
				on:click={(e) => {
					menuOpen = false;
				}}>close</i
			>
			<ul class="nav-items">
				<li class="nav-item">
					<a
						class:active={$page.url.pathname === '/'}
						sveltekit:prefetch
						class="nav-item__link"
						href="/">Home</a
					>
				</li>
				<li class="nav-item">
					<a
						class:active={$page.url.pathname === '/conversations'}
						class="nav-item__link"
						sveltekit:prefetch
						href="/conversations">Conversations</a
					>
				</li>
				<li class="nav-item">
					<a
						class:active={$page.url.pathname === '/polls'}
						class="nav-item__link"
						sveltekit:prefetch
						href="/polls">Polls</a
					>
				</li>
			</ul>
		</div>
	{/if}
</header>

<style lang="scss">
	@use '../../styles/partials/variables' as *;
	@use '../../styles/partials/mixins' as *;

	header {
		display: flex;
		justify-content: space-between;
		align-items: center;
		background-color: white;
		height: 56px;
		box-shadow: 0.2px 0.2px 10px 0 rgba($color: #000000, $alpha: 0.25);

		@include default-padding;

		.title {
			font-family: $font-primary;
			font-size: 20px;
		}

		.menubar {
			font-size: 24px;
			cursor: pointer;
		}

		.nav-items {
			display: none;

			@include desktop {
				display: flex;
				justify-content: space-between;
				align-items: center;
			}
		}

		.nav-overlay {
			height: 100vh;
			width: 100vw;
			background-color: rgba($color: #000000, $alpha: 0.65);
			position: fixed;
			top: 0;
			bottom: 0;
			left: 0;
			right: 0;

			.nav-items {
				font-size: 24px;
				list-style-type: none;
				position: fixed;
				top: 25vh;
				right: 14px;
				text-align: right;
			}

			.nav-item {
				font-family: $font-primary;
				margin-bottom: 36px;

				&__link {
					color: white;
					text-decoration: none;
				}
			}

			.nav-item .active {
				text-decoration: underline;
			}
		}

		.closeicon {
			position: fixed;
			top: 14px;
			right: 14px;
			font-size: 24px;
			color: white;
			cursor: pointer;
		}
	}
</style>
