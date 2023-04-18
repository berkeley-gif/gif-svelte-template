<script>
	import {
		Header,
		SkipToContent,
		HeaderUtilities,
		HeaderActionLink,
		HeaderNav,
		HeaderNavItem,
		Content
	} from "carbon-components-svelte";
	import LogoGithub from "carbon-icons-svelte/lib/UserAvatarFilledAlt.svelte";
	import "../../styles/main.scss";

	let isOpen = false;
	let isSideNavOpen = true;
</script>

<Header
	aria-label="Navigation"
	href="{'/'}"
	expandedByDefault="{true}"
	platformName="GIF SvelteKit Template"
	bind:isSideNavOpen="{isSideNavOpen}"
>
	<svelte:fragment slot="skip-to-content">
		<SkipToContent />
	</svelte:fragment>

	<HeaderNav>
		<HeaderNavItem href="/material" text="Using Svelte Material UI" />
		<HeaderNavItem href="/resources" text="Resources" />
	</HeaderNav>

	<HeaderUtilities>
		<HeaderActionLink
			icon="{LogoGithub}"
			href="https://github.com/berkeley-gif/cal-adapt-svelte-components"
			target="_blank"
		/>
	</HeaderUtilities>
</Header>

<Content>
	<slot />
</Content>
