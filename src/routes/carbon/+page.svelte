<script>
	import {
		Grid,
		Row,
		Column,
		CodeSnippet,
		Button,
		Link,
		DataTable
	} from "carbon-components-svelte";
	import { BarChartSimple } from "@carbon/charts-svelte";
	import "@carbon/charts/styles.css";
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
	<Row>
		<Column>
			<h1>Building with Carbon Components Svelte</h1>
			<p>Built with SvelteKit and Carbon Svelte Components</p>
		</Column>
	</Row>

	<Row style="margin: var(--cds-spacing-16) 0;">
		<Column>
			<h2 class="h4">Sample buttons</h2>
			<Row>
				<Column sm="{1}" md="{2}">
					<div style="padding: var(--cds-spacing-05) 0">
						<CodeSnippet type="inline" code="background-color: var(--cds-interactive-01)" />
					</div>
					<Button>Primary</Button>
				</Column>
				<Column sm="{1}" md="{2}">
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
				<Column sm="{1}" md="{4}">
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
