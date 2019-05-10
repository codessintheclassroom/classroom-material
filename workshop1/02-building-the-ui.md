[⏮ Previous step: Setup](./01-setup.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Connecting the API](./03-connecting-the-api.md)

----

## Step 2: Build a user interface for the animal shelter app

In this step, we'll use some popular libraries to help us create a user interface for our app.

### Context

There are several UI frameworks that we can use to make our life easier.
These frameworks will help us to create a good-looking UI for our React app
without needing to write our own stylesheets.

Some examples of these UI frameworks are: [Bootstrap], [Material-UI] or
[Office UI Fabric].

For this project, we suggest using Bootstrap, through its most popular React
bindings: [`react-bootstrap`].

### Install `react-bootstrap`

In a terminal (reminder: you can use `Terminal → New Terminal` from within VS Code):

1. To install the `react-bootstrap` library:

       npm install react-bootstrap @types/react-bootstrap

2. `react-bootstrap` only contains the UI components for React, but doesn't
   include any stylesheets. We need to add a reference to the Bootstrap CSS into
   the `<head>` section of your application's `index.html` (you'll find it in
   `public/index.html`):

       <link
           rel="stylesheet"
           href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
           integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T"
           crossorigin="anonymous"
       />

### Use the components from `react-bootstrap` to build a list view

Use the Bootstrap [component library][react-components] to build a listing of
all the animals hosted by the shelter. Here are some useful layouts and
components to consider:

- [Grid layout system](https://react-bootstrap.github.io/layout/grid/),
- [Cards](https://react-bootstrap.github.io/components/cards/),
- [Card layouts](https://react-bootstrap.github.io/components/cards/#card-layout)

If you're already familiar with React, go ahead and create your own design
using the image below as a guide. Feel free to improvise!

<p align="center">
<img src="https://user-images.githubusercontent.com/1350095/56684256-48f43600-66c7-11e9-9e9b-648d118fb76f.jpg" alt="smaple list view UI" width="400"/>
</p>

<details>
<summary><b>If you aren't familiar with React components or how to use them to build a UI,
click here to read more detailed instructions.
</b></summary><br>

### Adding a PetCard component

To visualise the details of a single pet we create a React component to represent the Pet "card".

1. Create a file in the `src\` directory called `PetCard.tsx`.

2. You can create a simple React component within this file that might look like this:

   ```tsx
   import React, { Component } from 'react';

   class PetCard extends Component {
     render() {
         return <div>I'm a pet card!</div>;
     }
   }

   export default PetCard;
   ```

3. Make the `render()` method do something a bit more interesting! For
   example, instead of returning a `<div>` with some text in, you could use the
   [`react-bootstrap`] `Card` component to represent one of our furry friends.

   Check out the [documentation for the `Card` component first][bst-cards].
   Note that you'll need to add imports for the components you use! (VS Code
   can help with this: try pressing `Ctrl + .` with the cursor on a component
   with a squiggly underline.)

   Your result might look like:

    ```tsx
    return (
      <Card style={{ width: '18rem' }}>
        <Card.Img variant="top" src={"https://source.unsplash.com/collection/212527/200x200/?sig=" + Math.floor(Math.random() * 100)} />
        <Card.Body>
          <Card.Title>{this.props.pet.name}</Card.Title>
          <Card.Text>{this.props.pet.description}</Card.Text>
          <Button variant="primary">Adopt</Button>
        </Card.Body>
      </Card>
    );
    ```

4. You'll also need to define the properties ("props") passed into the
   `PetCard` component. Update the start of your PetCard component to include a
   definition of the expected structure of a Pet, and the properties that will
   be passed into the component:

   ```tsx
   ...
   interface Pet {
     readonly id: string;
     name: string;
     description: string;
   }

   type Props = {
     pet: Pet;
   };

   class PetCard extends Component<Props> {
     ...
   ```

### Create a grid layout in the main page

In the main page of our application (`src\App.tsx`), we'll replace the boilerplate from `create-react-app` with our own grid layout to display multiple pets.

1. First of all, as we are not yet fetching the list of pets from the
   backend, let's create some data for fake pets so that we can test our
   layout. In `src\App.tsx`, after the imports but before `const App`, add
   something like the following:

   ```tsx
   var mockedPets = [
     { id: "1", name: "Berty", description: "Has a good nose for truffles" },
     { id: "2", name: "Argo", description: "A superhero (of the dog world)" },
     { id: "3", name: "Fred", description: "Has opinions about sausages" },
   ];
   ```

2. To create a grid view of the animals in the shelter, we can use some of
   the components Bootstrap offers such as `Container`, `Row` and `Col`. See
   [`react-bootstrap`'s grid docs][bst-grid] for more information.

   Here's one way you could choose to lay out the pets. This code replaces
   the code in the block under `const App: React.FC = () => {`:

   ```tsx
   return (
     <Container>
       <Row>
       <Col>
         <CardColumns>
         {
           mockedPets.map((pet) => <PetCard key={pet.id} pet={pet} />)
         }
         </CardColumns>
       </Col>
       </Row>
     </Container>
   );
   ```

   (Don't forget: VS Code can help you add imports for the components you
   use. Press `Ctrl + .` with the cursor on a component with a squiggly
   underline.)

3. Check your browser. Hopefully at this point you should be able to see a
   list of pets laid out nicely on your main page.
</details>

### Commit your changes

Hooray! You made a user interface for the pet shelter! 🥳 At this point, it
might make sense to save the progress you've made to the Git repository.

(If you need to, review the [guidance on staging changes and committing in the
Git cheatsheet](../git-cheatsheet.md#commit).)

For example:

    git add -A .
    git commit

When you are done, you can continue by [connecting your interface up to the
animal shelter API](./03-connecting-the-api.md).

[Bootstrap]: https://getbootstrap.com/
[`react-bootstrap`]: https://react-bootstrap.github.io/
[Material-UI]: https://material-ui.com/
[Office UI Fabric]: https://developer.microsoft.com/en-us/fabric
[bst-cards]: https://react-bootstrap.github.io/components/cards/
[bst-grid]: https://react-bootstrap.github.io/layout/grid/
[react-components]: https://reactjs.org/docs/components-and-props.html

----

[⏮ Previous step: Setup](./01-setup.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Connecting the API](./03-connecting-the-api.md)