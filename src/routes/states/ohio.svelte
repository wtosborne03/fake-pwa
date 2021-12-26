<script>
  import { Container, Card, CardBody, Form, FormGroup, Label, Input, Button } from 'sveltestrap';
    let firstname = '';
    let middlename = '';
    let lastname = '';
    let dl = '00290190';
    let eye = '';
    let sexGroup = 'M';
    let streetAddress = '';
    let city = '';
    let zip = '';
    let dob;
    let iss;
    let exp;
    function gen(event) {
        dob = dob.replace(/\//g, '-');
        iss = iss.replace(/\//g, '-');
        exp = exp.replace(/\//g, '-');

        streetAddress.toUpperCase();
        event.preventDefault();
        
        var code = "@\
\n\
AA" + sexGroup +  "VA6360250101DL" + dl + "DAQUD386991\n\
DAA" + firstname +" " + middlename + " " + lastname +"\n\
DAG" + streetAddress + "\n\
DAI" + city +"\n\
DAJOH\n\
DAK" + zip + "\n\
DARD\n\
DAS/\n\
DAT---- \n\
DAU502\n\
DAY" + eye + "\n\
DBA" + exp + "\n\
DBB" + dob + "\n\
DBCF\n\
DBD" + iss + "\n\
DBF00\n\
DBHN";

        var canvas = document.getElementById("barcode")
        PDF417.draw(code, canvas, 3, 1, 4)
    }
    
</script>

<FormGroup>
    <Label for="exampleEmail">First Name</Label>
    <Input
      autocomplete="given-name"
      placeholder="First Name"
      bind:value={firstname}
    />
  </FormGroup>
  <FormGroup>
      <Label for="exampleEmail">Middle Name</Label>
      <Input
        autocomplete="additional-name"
        placeholder="Middle Name"
        bind:value={middlename}
      />
  </FormGroup>
  <FormGroup>
      <Label for="exampleEmail">Last Name</Label>
      <Input
          autocomplete="family-name"
          placeholder="Last Name"
          bind:value={lastname}
      />
  </FormGroup>
  <FormGroup>
      <Label for="exampleEmail">Street Address</Label>
      <Input
          autocomplete="street-address"
          placeholder="Street Address"
          bind:value={streetAddress}
      />
  </FormGroup>
  <FormGroup>
      <Label for="exampleEmail">City</Label>
      <Input
          autocomplete="address-level2"
          placeholder="City"
          bind:value={city}
      />
  </FormGroup>
  <FormGroup>
      <Label for="exampleEmail">Zip Code</Label>
      <Input
          autocomplete="postal-code"
          placeholder="Zip Code"
          bind:value={zip}
      />
  </FormGroup>
  <FormGroup>
      <Label for="exampleEmail">Driver's License Number</Label>
      <Input
          placeholder="Dl#"
          bind:value={dl}
      />
  </FormGroup>
  <FormGroup>
      <Label for="exampleSelect">Eye Color</Label>
      <Input type="select" name="select" id="exampleSelect" bind:value={eye}>
        <option>BLU</option>
        <option>BRN</option>
        <option>GRN</option>
        <option>GRY</option>
        <option>BLK</option>
        <option>HZL</option>
      </Input>
  </FormGroup>
  <FormGroup>
      <Label>Gender</Label>
      <Input
        id="r1"
        type="radio"
        bind:group={sexGroup}
        value="M"
        label="Male"
        default
      />
      <Input
        id="r2"
        type="radio"
        bind:group={sexGroup}
        value="F"
        label="Female"
      />
    </FormGroup>
    <FormGroup>
        <Label>Date of Birth</Label>
        <input type="date" id="dob" bind:value={dob}>
    </FormGroup>
    <FormGroup>
        <Label>Issue Date</Label>
        <input type="date" id="dob" bind:value={iss}>
    </FormGroup>  
    <FormGroup>
        <Label>Expiry date</Label>
        <input type="date" id="dob" bind:value={exp}>
    </FormGroup>  
  <Button color="primary" on:click={gen} >Generate</Button>