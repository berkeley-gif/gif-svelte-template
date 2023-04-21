<script>
	import LayoutGrid, { Cell as LayoutCell } from "@smui/layout-grid";
	import Button, { Label } from "@smui/button";
	import DataTable, { Head, Body, Row, Cell } from "@smui/data-table";
	import "../../styles/_theme_with_material.scss";
</script>

<LayoutGrid>
	<LayoutCell span="{12}">
		<h1>Building with Svelte Material UI</h1>
		<p>Built with SvelteKit and Carbon Svelte Components</p>
	</LayoutCell>

	<LayoutCell span="{12}">
		<h2 class="h4">Sample buttons</h2>
		<Button variant="raised">
			<Label>Raised</Label>
		</Button>
		<Button variant="unelevated">
			<Label>Unelevated</Label>
		</Button>
		<Button variant="outlined">
			<Label>Outlined</Label>
		</Button>
		<Button color="secondary" variant="raised">
			<Label>Raised</Label>
		</Button>
		<Button color="secondary" variant="unelevated">
			<Label>Unelevated</Label>
		</Button>
		<Button color="secondary" variant="outlined">
			<Label>Outlined</Label>
		</Button>
	</LayoutCell>

	<LayoutCell span="{12}">
		<h2 class="h4">Sample DataTable</h2>
		<DataTable table$aria-label="People list" style="max-width: 100%;">
			<Head>
				<Row>
					<Cell>Name</Cell>
					<Cell>Favorite Color</Cell>
					<Cell numeric>Favorite Number</Cell>
				</Row>
			</Head>
			<Body>
				<Row>
					<Cell>Steve</Cell>
					<Cell>Red</Cell>
					<Cell numeric>45</Cell>
				</Row>
				<Row>
					<Cell>Sharon</Cell>
					<Cell>Purple</Cell>
					<Cell numeric>5</Cell>
				</Row>
				<Row>
					<Cell>Rodney</Cell>
					<Cell>Orange</Cell>
					<Cell numeric>32</Cell>
				</Row>
				<Row>
					<Cell>Mack</Cell>
					<Cell>Blue</Cell>
					<Cell numeric>12</Cell>
				</Row>
			</Body>
		</DataTable>
	</LayoutCell>
	<LayoutCell>
		<p>Back to:</p>
		<ul>
			<li>
				<a href="/carbon">Using & Styling with Carbon Components Svelte</a>
			</li>
			<li>
				<a href="/">Home</a>
			</li>
		</ul>
	</LayoutCell>
</LayoutGrid>
