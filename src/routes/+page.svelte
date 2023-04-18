<script>
	import { Grid, Row, Column, ClickableTile } from "carbon-components-svelte";
</script>

<Grid>
	<Row>
		<Column>
			<h1>Welcome to the GIF SvelteKit Template</h1>
		</Column>
	</Row>

	<Row style="margin-bottom: var(--cds-spacing-16)">
		<Column sm="{1}" md="{2}">
			<ClickableTile href="/carbon">Carbon Components Svelte</ClickableTile>
		</Column>
		<Column sm="{1}" md="{2}">
			<ClickableTile href="/material">Svelte Material UI</ClickableTile>
		</Column>
	</Row>
</Grid>
