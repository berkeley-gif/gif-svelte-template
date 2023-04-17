<script>
    import { Grid, Row, Column, CodeSnippet } from "carbon-components-svelte";
    import { Button } from "carbon-components-svelte";
  </script>

 <Grid>

    <Row >
        <Column>
            <h1>Welcome to the GIF SvelteKit Template</h1>
            <p>Built with SvelteKit and Carbon Svelte Components</p>
        </Column>
    </Row>

    <Row>
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
    
  </Grid>
 




 