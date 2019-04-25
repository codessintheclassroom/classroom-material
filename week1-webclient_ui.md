# Codess in the Classroom - Week 1: The Web Client

## Building the Pet Shelter UI

There are several UI frameworks that can be used to have a good-looking UI with React without
the need of manually writing style instructions.
For instance, one can use [Bootstrap][bootstrap], [Material-UI][material-ui] or [Office UI Fabric][office-ui-fabric]. For this project, we suggest using Bootstrap, through its most popular React bindings: [react-boostrap][react-bootstrap].

1. Run `npm install react-bootstrap @types/react-bootstrap` to install the `react-boostrap` library.
2. Reference the bootstrap css file in the HTML index file located in `public/index.html` as follows.

        <link
            rel="stylesheet"
            href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
            integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T"
            crossorigin="anonymous"
        />

3. Use the Bootstrap component library to build a simple view for all the animals hosted by the shelter. Here are some useful layouts and components to consider:  
    - Grid layout system: https://react-bootstrap.github.io/layout/grid/
    - Cards: https://react-bootstrap.github.io/components/cards/
    - Card Layouts: https://react-bootstrap.github.io/components/cards/#card-layout


An example of the view is shown in the image below - though, by all means, feel free to come up with anything that looks different.

<p align="center"> 
<img src="https://user-images.githubusercontent.com/1350095/56684256-48f43600-66c7-11e9-9e9b-648d118fb76f.jpg" alt="smaple list view UI" width="400"/>
</p>

 ----
<details>
<summary><b>Click here to read more hints on how to construct the UI</b></summary><br>

**Adding a PetCard component**  
To visualise the details of a single pet we create a separate React component. 
In `src\PetCard.js`, we create a `PetCard` component class, which, in the `render()`
method, will return a simple set of Bootstrap components that constitute the *identity card* of our furry friend. To do that, you may want to check out the docs of the `Card` component, [here][bst-cards].
An excerpt of the result may look like this:

```jsx
<Card style={{ width: '18rem' }}>
    <Card.Img variant="top" src={"https://source.unsplash.com/collection/212527/200x200/?sig=" + Math.floor(Math.random() * 100)} />
    <Card.Body>
        <Card.Title>{props.pet.name}</Card.Title>
        <Card.Text>{props.pet.description}</Card.Text>
        <Button variant="primary">Adopt</Button>
    </Card.Body>
</Card>
```

**Creating a grid layout in the main page**  
In the main page of our application - which is `App.js` - let's add some simple layout components.
To do so, Bootstrap offers several ready-made components that we can combine to create a grid view of 
all the pets in the shelter. In particular, you can add to the `render()` method components such as 
`Container`, `Row` and `Col` - see the [grid docs][bst-grid] of react-boostrap for more information.
    
**Adding pets to our main page**  
Since we cannot yet fetch the list of pets from the backend, to test our layout
we create some data of fake pets, as follows.

```jsx
var mockedPets = [
    { name: "Berty", description: "Has a good nose for truffles" },
    { name: "Argo", description: "A superhero (in dogs' world)" },
    { name: "Fred", description: "Has opinions about sausages" },
]
```

Now we can map each of these fake pets' data to a `PetCard` component in the `render()` method
of our main page.

```jsx 
<Container>
    <Row>
    <Col>
        <CardColumns>
        {
            mockedPets.map((pet) => {
                return (
                    <PetCard key={pet.id} pet={pet} />
                );
            })
        }
        </CardColumns>
    </Col>
    </Row>
</Container>
```
Congratulations, at this point you should be able to see a list of pets layed out nicely on your main page.

</details>

When you are done, you should **commit** your work and continue by adding the calls to the backend, as described here **TODO: ADD LINk**.  

 [bootstrap]: https://getbootstrap.com/
 [react-bootstrap]: https://react-bootstrap.github.io/
 [material-ui]: https://material-ui.com/
 [office-ui-fabric]: https://developer.microsoft.com/en-us/fabric
 [bst-cards]: https://react-bootstrap.github.io/components/cards/
 [bst-grid]: https://react-bootstrap.github.io/layout/grid/