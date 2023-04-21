<script>
	import { browser } from "$app/environment";
	import {
		Grid,
		Row,
		Column,
		CodeSnippet,
		Button,
		Link,
		DataTable,
		RadioButtonGroup,
		RadioButton
	} from "carbon-components-svelte";
	import { BarChartSimple } from "@carbon/charts-svelte";
	import "@carbon/charts/styles.css";

	let theme = "white";

	function updateFallbackTheme(e) {
		if (!browser) return;
		document.documentElement.setAttribute("theme", e.detail);
	}
</script>

<style lang="scss">
	ul {
		margin-left: var(--cds-spacing-08);
		list-style-type: disc;
	}

	ul li {
		padding: var(--cds-spacing-02) 0;
	}
</style>

<Grid>
	<Row style="margin-bottom: var(--cds-spacing-06);">
		<Column>
			<h1>Building with Carbon Components Svelte</h1>
			<p>
				The Carbon Components Svelte library implements the Carbon Design System. To learn more
				about customizing styles for the Carbon Components Svelte library read the section on
				Theming below.
			</p>
			<RadioButtonGroup
				on:change="{updateFallbackTheme}"
				legendText="Use a different fallback Carbon themes"
				selected="{theme}"
			>
				{#each ["white", "g10", "g80", "g90", "g100"] as value}
					<RadioButton labelText="{value}" value="{value}" />
				{/each}
			</RadioButtonGroup>
		</Column>
	</Row>

	<Row style="margin: var(--cds-spacing-16) 0;">
		<Column>
			<h2 class="h4">Sample buttons</h2>
			<Row>
				<Column sm="{1}" md="{4}">
					<div style="padding: var(--cds-spacing-05) 0">
						<CodeSnippet type="inline" code="background-color: var(--cds-interactive-01)" />
					</div>
					<Button>Primary</Button>
				</Column>
				<Column sm="{1}" md="{4}">
					<div style="padding: var(--cds-spacing-05) 0">
						<CodeSnippet type="inline" code="background-color: var(--cds-interactive-02)" />
					</div>
					<Button kind="secondary">Secondary</Button>
				</Column>
			</Row>
		</Column>
	</Row>
	<hr />

	<Row style="margin: var(--cds-spacing-16) 0;">
		<Column>
			<h2 class="h4">Data Table</h2>
			<Row>
				<Column>
					<DataTable
						zebra
						headers="{[
							{ key: 'name', value: 'Name' },
							{ key: 'protocol', value: 'Protocol' },
							{ key: 'port', value: 'Port' },
							{ key: 'rule', value: 'Rule' }
						]}"
						rows="{[
							{
								id: 'a',
								name: 'Load Balancer 3',
								protocol: 'HTTP',
								port: 3000,
								rule: 'Round robin'
							},
							{
								id: 'b',
								name: 'Load Balancer 1',
								protocol: 'HTTP',
								port: 443,
								rule: 'Round robin'
							},
							{
								id: 'c',
								name: 'Load Balancer 2',
								protocol: 'HTTP',
								port: 80,
								rule: 'DNS delegation'
							},
							{
								id: 'd',
								name: 'Load Balancer 6',
								protocol: 'HTTP',
								port: 3000,
								rule: 'Round robin'
							},
							{
								id: 'e',
								name: 'Load Balancer 4',
								protocol: 'HTTP',
								port: 443,
								rule: 'Round robin'
							},
							{
								id: 'f',
								name: 'Load Balancer 5',
								protocol: 'HTTP',
								port: 80,
								rule: 'DNS delegation'
							}
						]}"
					/>
				</Column>
			</Row>
		</Column>
	</Row>
	<hr />

	<Row style="margin: var(--cds-spacing-16) 0;">
		<Column>
			<h2 class="h4">Sample line chart</h2>
			<Row>
				<Column sm="{1}" md="{4}">
					<BarChartSimple
						data="{[
							{ group: 'Qty', value: 65000 },
							{ group: 'More', value: 29123 },
							{ group: 'Sold', value: 35213 },
							{ group: 'Restocking', value: 51213 },
							{ group: 'Misc', value: 16932 }
						]}"
						options="{{
							title: 'Simple bar (discrete)',
							height: '400px',
							axes: {
								left: { mapsTo: 'value' },
								bottom: { mapsTo: 'group', scaleType: 'labels' }
							}
						}}"
					/>
				</Column>
			</Row>
		</Column>
	</Row>
	<hr />

	<Row style="margin: var(--cds-spacing-16) 0;">
		<Column>
			<h2 class="h4">Quotation</h2>
			<Row>
				<Column sm="{1}" md="{8}">
					<figure class="quote svelte-11vvs0c">
						<blockquote cite="https://www.climateassessment.ca.gov/">
							<p class="svelte-11vvs0c">
								California is one of the most 'climate-challenged' regions of North America; its
								historical climate is extremely variable, and climate change is making extreme
								conditions more frequent and severe. California’s temperatures are already warming,
								heat waves are more frequent, and precipitation continues to be highly variable.
							</p>
						</blockquote>
						<figcaption>
							<cite
								>— A Summary of Key Findings from California’s Fourth Climate Change Assessment</cite
							>
						</figcaption>
					</figure>
				</Column>
			</Row>
		</Column>
	</Row>
	<hr />

	<Row>
		<Column>
			<h2>Theming</h2>
			<p>
				There are currently two ways to <a
					href="https://github.com/carbon-design-system/carbon-components-svelte#styling"
					>apply custom styles</a
				> to the components:
			</p>
			<ul>
				<li>
					<h5>Using SCSS files from carbon-components library</h5>
					<p>
						The <code class="bx--snippet code">src/styles/themes/caladapt</code> folder in this repo
						shows how to implement custom styles using SCSS files from
						<code class="bx--snippet code">carbon-components</code> repo.
					</p>
				</li>
				<li>
					<h5>Using CSS</h5>
					<p>
						The <code class="bx--snippet code">src/styles/themes/with-open-props</code> folder in
						this repo shows how to implement custom styles using CSS from the from
						<code class="bx--snippet code">carbon-components-svelte</code>
						repo and a different CSS library called
						<a href="https://open-props.style/">open props</a>.
					</p>
				</li>
			</ul>
			<p>
				Hopefully theming with SCSS will get a little easier once Carbon v11 style integration is
				completed in the <a
					href="https://github.com/carbon-design-system/carbon-components-svelte/issues/1629"
					>Carbon Components Svelte library</a
				>.
			</p>
		</Column>
	</Row>
	<hr />

	<Row>
		<Column>
			<h2>Resources</h2>
			<h3 class="h4">GIF</h3>
			<ul>
				<li>
					<Link href="https://github.com/berkeley-gif/cal-adapt-svelte-components">
						Cal-Adapt Svelte Component Library
					</Link>
				</li>
				<li>
					<Link href="https://github.com/berkeley-gif/caladapt-website-2021">
						Cal-Adapt 2.0 using Sapper and Svelte
					</Link>
				</li>
			</ul>
			<h3 class="h4">Carbon Design System</h3>
			<ul>
				<li>
					<Link href="https://github.com/berkeley-gif/cal-adapt-svelte-components">
						Cal-Adapt Svelte Component Library
					</Link>
				</li>
				<li>
					<Link href="https://carbon-components-svelte.onrender.com/">
						Carbon Components Svelte
					</Link>
				</li>
				<li>
					<Link href="https://charts.carbondesignsystem.com/svelte/?path=/story/intro--welcome">
						Carbon Charts Svelte
					</Link>
				</li>
				<li>
					<Link href="https://www.carbondesignsystem.com/">Carbon Design System</Link>
				</li>
				<li>
					<Link href="https://carbondesignsystem.com/data-visualization/getting-started/">
						Carbon Data Visualization
					</Link>
				</li>
				<li>
					<Link href="https://www.ibm.com/design/language/">IBM Design Language</Link>
				</li>
			</ul>
		</Column>
	</Row>
</Grid>
