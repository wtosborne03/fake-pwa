<script>
  import { Container, Card, CardBody, Form, FormGroup, Label, Input, Button } from 'sveltestrap';
  import Ohio from './states/ohio.svelte';
  import { onMount } from 'svelte';
  let state = "Ohio";
  onMount(() => {
    var canvas = document.getElementById('barcode');
    var heightRatio = 1.5;
    canvas.height = canvas.width * heightRatio;

  });
  
</script>
<style>
  #barcode {
  width: 100%;
}
</style>
<Container>
    <Card style="margin:25px;">
        <CardBody>
            <h1 style="display:inline-block">Fake Barcode Generator</h1>
            <Button style="margin-left: 1em; margin-bottom: 1em;"color="info" on:click={share} > Share </Button>
            <Form>
                <FormGroup>
                    <Label for="exampleSelect">State</Label>
                    <Input type="select" name="select" id="exampleSelect" bind:value={state}>
                      <option>Ohio</option>
                    </Input>
                </FormGroup>
                {#if state =='Ohio'}
                  <Ohio></Ohio>
                {:else if state == 'connecticut'}
                {/if}
                
            </Form>
            <canvas id="barcode"></canvas>
        </CardBody>
    </Card>
</Container>