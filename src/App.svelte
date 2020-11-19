<script>
  import 'bulma/css/bulma.css'
  import student from './data/student.json'

  import { onMount } from 'svelte'

  export let name

  import { Button, Label, Input, Table, Col, Container, Row } from 'sveltestrap'

  onMount(() => {})

  let datas = []

  let fields = {
    studentNumber: '',
    firstName: '',
    lastName: '',
    department: '',
    age: '',
  }

  const addStudent = () => {
    datas.push(fields)
    console.log('data', datas)
  }
</script>

<style>
  .mainContainer {
    text-align: center;
    padding: 1em;
    width: 100%;
    margin: 0 auto;
  }

  .tableSection {
    width: 100%;
    display: flex;
    margin-top: 20px;
    justify-content: center;
    position: relative;
  }

  .formSection {
    text-align: left;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
</style>

<div class="mainContainer">
  <h1>Hello {name}!</h1>
  <p>
    Visit the
    <a href="https://svelte.dev/tutorial">Svelte tutorial</a>
    to learn how to build Svelte apps.
  </p>

  <form on:submit={addStudent}>
    <Container>
      <Row>
        <Col sm="6">
          <div class="formSection">
            <div>
              <Label>Student Number</Label>
              <Input name="studentNumber" bind:value={fields.studentNumber} />
            </div>
          </div>
        </Col>
      </Row>

      <Row>
        <Col xl="3">
          <div class="formSection">
            <div>
              <Label>First Name</Label>
              <Input name="firstname" bind:value={fields.firstName} />
            </div>
          </div>
        </Col>
      </Row>
    </Container>

    <Button type="submit" color="primary">Submit</Button>
  </form>

  <div class="tableSection">
    <Table striped>
      <thead>
        <tr>
          <th>#</th>
          <th>Name</th>
          <th>Age</th>
          <th>Department</th>
          <th>Year Level</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        {#each student as data}
          <tr>
            <td>{data.studentNumber}</td>
            <td>{data.firstName}</td>
            <td>{data.age}</td>
            <td>{data.department}</td>
            <td>{data.yearLevel}</td>
            <td>
              <Button outline color="primary">EDIT</Button>
              <Button color="danger">DELETE</Button>
            </td>
          </tr>
        {/each}
      </tbody>
    </Table>
  </div>
</div>
