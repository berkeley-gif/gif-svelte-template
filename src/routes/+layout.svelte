<script>
	import {
	  Header,
	  HeaderUtilities,
	  HeaderAction,
	  HeaderActionLink,
	  HeaderPanelLinks,
	  HeaderPanelLink,
	  HeaderPanelDivider,
	  SkipToContent,
	  Content,
	} from "carbon-components-svelte";
	import LogoGithub from "carbon-icons-svelte/lib/LogoGithub.svelte";
	import "../styles/main.scss";
  
	let isOpen = false;
	let isSideNavOpen = true;
  </script>
  
  <Header
	aria-label="Navigation"
	href="{'/'}"
	expandedByDefault="{true}"
	bind:isSideNavOpen="{isSideNavOpen}"
  >
	<svelte:fragment slot="skip-to-content">
	  <SkipToContent />
	</svelte:fragment>
  
	<HeaderUtilities>
	  <HeaderActionLink
		icon="{LogoGithub}"
		href="https://github.com/berkeley-gif/cal-adapt-svelte-components"
		target="_blank"
	  />
	  <HeaderAction transition="{false}" bind:isOpen="{isOpen}">
		<HeaderPanelLinks>
		  <HeaderPanelDivider>GIF portfolio</HeaderPanelDivider>
		  <HeaderPanelLink
			href="https://github.com/carbon-design-system/carbon-icons-svelte"
		  >
			Svelte starter template for GIF projects
		  </HeaderPanelLink>
		  <HeaderPanelLink
			href="https://github.com/berkeley-gif/caladapt-website-2021"
		  >
			Cal-Adapt 2.0 using Sapper and Svelte
		  </HeaderPanelLink>
		  <HeaderPanelDivider>Resources</HeaderPanelDivider>
		  <HeaderPanelLink href="https://www.carbondesignsystem.com/">
			Carbon Design System
		  </HeaderPanelLink>
		  <HeaderPanelLink href="https://www.ibm.com/design/language/">
			IBM Design Language
		  </HeaderPanelLink>
		</HeaderPanelLinks>
	  </HeaderAction>
	</HeaderUtilities>
  </Header>

  <Content>
  	<slot />
  </Content>
  

