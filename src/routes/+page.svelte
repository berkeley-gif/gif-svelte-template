<script>
    import { Grid, Row, Column, CodeSnippet, Button } from "carbon-components-svelte";
    import { BarChartSimple } from "@carbon/charts-svelte";
    import "@carbon/charts/styles.css";
  </script>

 <Grid>

    <Row>
        <Column>
            <h1>Welcome to the GIF SvelteKit Template</h1>
            <p>Built with SvelteKit and Carbon Svelte Components</p>
        </Column>
    </Row>

    <Row  style="margin-bottom: var(--cds-spacing-16)">
        <Column>
            <h2 class="h4">Sample buttons</h2>
            <Row>
                <Column sm={1} md={2}>
                    <div style="padding: var(--cds-spacing-05) 0">
                        <CodeSnippet type="inline" code="background-color: var(--cds-interactive-01)"  />
                    </div>
                    <Button>Primary</Button>
                </Column>
                <Column sm={1} md={2}>
                    <div style="padding: var(--cds-spacing-05) 0">
                        <CodeSnippet type="inline" code="background-color: var(--cds-interactive-02)"  />
                    </div>
                    <Button kind="secondary">Secondary</Button>
                </Column>
            </Row>
        </Column>
    </Row>

    <Row  style="margin-bottom: var(--cds-spacing-16)">
        <Column>
            <h2 class="h4">Sample line chart</h2>
            <Row>
                <Column sm={1} md={4}>
                    <BarChartSimple
  data={[
    { group: "Qty", value: 65000 },
    { group: "More", value: 29123 },
    { group: "Sold", value: 35213 },
    { group: "Restocking", value: 51213 },
    { group: "Misc", value: 16932 },
  ]}
  options={{
    title: "Simple bar (discrete)",
    height: "400px",
    axes: {
      left: { mapsTo: "value" },
      bottom: { mapsTo: "group", scaleType: "labels" },
    },
  }}
/>
                </Column>
            </Row>
        </Column>
    </Row>
    
  </Grid>
 




 