[⏮ Previous step: Building the UI](./02-building-the-ui.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Testing your code](./04-testing-your-code.md)

----

## Step 3: Connect the user interface to the shelter API

In this part of the workshop, we are going to connect our frontend
application to a backend API. This will allow us to retrieve the list of
animals available for adoption.

### Context

As discussed in the previous section, a SPA is a single-page application,
where all of the behaviours of the user interface are defined in the
frontend. In order to fetch data (like the list of animals available for
adoption), store data (such as a description of a new animal) and perform
useful actions (like submitting a request to adopt an animal!) a SPA will
typically talk to an API (Application Programming Interface).

In the abstract, an API is an interface which defines how two or more
computer systems can interact. Concretely, an API can be a service which
accepts requests from clients ("API clients") to retrieve, store, and modify
data which is exposed through the API.

We're going set up our SPA as a client for a backend service (the API) which
speaks HTTP, the protocol of the web. The SPA will request data on available
animals from the API by making HTTP requests to the backend.

Luckily for you, the backend service already exists! You'll be wiring up the
code you've already written so that it pulls data from the API instead of
using the dummy data (`mockedPets`) you created in the previous step.

The API is described by the [API specification], and is hosted at:

    https://codess-shelter.azurewebsites.net/api/v1/

### Making HTTP calls from the frontend application

There are several third party libraries that can be used for making HTTP
requests in Javascript (e.g. [Request] or [Axios]). For this workshop, we
suggest relying on the native Javascript [`fetch`] API, which is available in
most modern browsers.

To get the list of pets available, we need to:

1. Make an HTTP GET request to `https://codess-shelter.azurewebsites.net/api/v1/pets`,
2. Parse the response,
3. Use the response as the state for our frontend app.

If you're familiar with [`fetch`] and React, you may wish to try to set this
up without further hints, but more guidance is available by expanding the
section below.

<details>
<summary><b>If you'd like further guidance on hooking the frontend up to the API, click here.</b></summary>

### Sharing the "Pet" model between components

We're going to need to have a common understanding of what a "Pet" object
looks like across different parts of our code. Now is a good time to extract
the `Pet` interface you created in the previous section into its own module.

1. Move the `Pet` interface, i.e. this code

   ```tsx
   interface Pet {
       readonly id: string;
       name: string;
       description: string;
   };
   ```

   into its own file, `src\Pet.tsx`.

2. You will also need to export the interface, so your `src\Pet.tsx` will
   look something like this:

   ```tsx
   export default interface Pet {
       readonly id: string;
       name: string;
       description: string;
   };
   ```

3. Update your `src\PetCard.tsx` file to import this interface. (Reminder:
   the lightbulb in VS Code can help with this!)

4. You may also wish to compare this definition of a "Pet" object with what
   is returned from the API and update it with some additional fields.

### Fetching the list of pets

Now you're going to update `src\App.tsx` so that the list of pets is stored
as application state, and is fetched when the page first loads.

1. At the beginning of your app component, i.e. under `const App: React.FC =
   () => {`, declare a state variable to hold an array of pets. The array is
   empty, for now:

   ```tsx
   const [pets, setPets] = useState<Array<Pet>>([]);
   ```

   _The `<Array<Pet>>` syntax is a TypeScript type annotation, and will help
   you to ensure that your state variable contains the data you expect._

   You'll need to update your imports: `useState` comes from `react` and
   `Pet` will come from the `Pet.tsx` file you just created:

   ```tsx
   import React, { useState } from 'react'
   ...
   import Pet from './Pet';
   ```

2. Immediately after our call to `useState`, we're going use a React "hook"
   called [`useEffect`](https://reactjs.org/docs/hooks-effect.html) to
   trigger a request to the API when the app first starts up:

   ```tsx
   useEffect(() => {
       const updatePets = async () => {
           const response = await fetch(`https://codess-shelter.azurewebsites.net/api/v1/pets`);
           const pets = await response.json();
           setPets(pets);
       };

       updatePets();
   }, []);
   ```

   _The nested function `updatePets` exists because we can't pass an `async` function to `useEffect`. Also, don't omit the second parameter to `useEffect`: it's important!_

3. Update the template returned by your app component to reference the `pets`
   state variable instead of `mockedPets`.

</details>

### Commit your changes

Hopefully at this point you have your frontend loading pet data from the pet
shelter API! 🥳 It's time to commit your progress again!

(You can review the [guidance on staging changes and committing in the Git
cheatsheet](../git-cheatsheet.md#commit).)

When you are done, you can continue by [learning how to test your
code](./04-testing-your-code.md).

### Bonus material: inquiry form

You might have noticed that the API has a [Submit Enquiry API endpoint], for
sending in requests to adopt these lovely animals.

If you're interested in learning more about React and about talking to APIs
from frontend code, adding an inquiry form to your app would be a great
exercise!

<details>
<summary><b>Click here to see a few suggestions to help you along the way.</b></summary>

- You could reate a [modal form][react-bst-modal] component, with fields to
  be filled out by the inquirer. (You'll want to check what fields are
  accepted by the API).

- Wire up the submit button of the modal (the `onClick` event) to make an
  HTTP POST request to the [Submit Enquiry API endpoint].

- Be aware that you'll need to extract the user data from the form component,
  so you probably want to treat that data as component state.

- You'll also need to ensure that you're allowing `fetch` to make
  cross-origin requests, using the `mode: "cors",` option. See [Supplying
  request options] for details.

- You could use a message at the bottom of the form (using the [conditional
  rendering] feature of React) to display a message showing the status of
  form submission.

</details>

[API specification]: https://codessintheclassroom.github.io/api-reference-solution/
[request]: https://github.com/request/request
[axios]: https://github.com/axios/axios
[`fetch`]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
[react-bst-modal]: https://react-bootstrap.github.io/components/modal/
[conditional rendering]: https://reactjs.org/docs/conditional-rendering.html#inline-if-else-with-conditional-operator
[Submit Enquiry API endpoint]: https://codessintheclassroom.github.io/api-reference-solution/#/inquiries/inquiries_add_v1
[Supplying request options]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch#Supplying_request_options

----

[⏮ Previous step: Building the UI](./02-building-the-ui.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Testing your code](./04-testing-your-code.md)