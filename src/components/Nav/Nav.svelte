<script>
	import defenseUnicornsLogo from '../../images/svg/doug.svg';
	import Mobile from './MobileNav.svelte';
	import Dropdown from './Dropdown.svelte';
	import InternalButton from '../InternalButton.svelte';

	let innerWidth = 0;
	$: isMobile = innerWidth < 1200;
</script>

<svelte:window bind:innerWidth />

{#if isMobile}
	<Mobile />
{:else}
	<nav>
		<div class="flex-grid">
			<div class="logo">
				<a href="/">
					<img src={defenseUnicornsLogo} alt="logo" loading="lazy" />
				</a>
			</div>
			<div class="links">
				<Dropdown />
				<a class="link" href="/Projects">Open Source</a>
				<a class="link" href="/Contracts">Contracts</a>
				<a class="link" href="/CaseStudies">Case Studies</a>
				<a class="link" href="/UnicornAcademy">Unicorn Academy</a>
			</div>
			<div class="button">
				<InternalButton link="/ContactUs" text="Request Demo" />
			</div>
		</div>
	</nav>
{/if}

<style>
	.flex-grid {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 0;
	}

	.logo {
		flex: 1;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.links {
		display: flex;
		gap: 1rem;
	}

	.link {
		text-decoration: none;
		cursor: pointer;
		position: relative;
		display: flex;
		align-items: center;
		color: white;
		font-size: 22px;
		white-space: nowrap;
	}

	.link:hover {
		text-decoration: none;
		color: #ffd700;
	}

	.link::before {
		content: '';
		position: absolute;
		width: 100%;
		height: 3px;
		bottom: -4px;
		left: 0;
		background: linear-gradient(to right, #ffd700, #ffa500);
		visibility: hidden;
		transform: scaleX(0);
		transition: all 0.3s ease-in-out;
	}

	.link:hover::before {
		visibility: visible;
		transform: scaleX(1);
	}

	.logo img {
		width: 60px;
		height: 85px;
		transition: all 0.3s ease-in-out;
	}

	.logo:hover img {
		width: 65px;
		height: 90px;
	}

	.button {
		flex: 1;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	@media only screen and (max-width: 1200px) {
		.logo img {
			height: 3rem;
		}

		.flex-grid {
			padding: 0 1rem;
		}
	}
</style>
