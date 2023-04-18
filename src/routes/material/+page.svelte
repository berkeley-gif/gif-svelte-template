<script>
	import { Grid, Row, Column } from "carbon-components-svelte";
	import Button, { Label } from "@smui/button";
	import "../../styles/_theme_with_material.scss";
</script>

<Grid>
	<Row>
		<Column>
			<h1>Building with Svelte Material UI</h1>
			<p>Built with SvelteKit and Carbon Svelte Components</p>
		</Column>
	</Row>

	<Row style="margin-bottom: var(--cds-spacing-16)">
		<Column>
			<h2 class="h4">Sample buttons</h2>
			<Row>
				<Column>
					<Button on:click="{() => clicked++}" variant="raised">
						<Label>Raised</Label>
					</Button>
					<Button on:click="{() => clicked++}" variant="unelevated">
						<Label>Unelevated</Label>
					</Button>
					<Button on:click="{() => clicked++}" variant="outlined">
						<Label>Outlined</Label>
					</Button>
					<Button color="secondary" on:click="{() => clicked++}" variant="raised">
						<Label>Raised</Label>
					</Button>
					<Button color="secondary" on:click="{() => clicked++}" variant="unelevated">
						<Label>Unelevated</Label>
					</Button>
					<Button color="secondary" on:click="{() => clicked++}" variant="outlined">
						<Label>Outlined</Label>
					</Button>
				</Column>
			</Row>
		</Column>
	</Row>
</Grid>
