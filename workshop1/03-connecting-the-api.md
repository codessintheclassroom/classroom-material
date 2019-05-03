[⏮ Previous step: Building the UI](./02-building-the-ui.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Testing your code](./04-testing-your-code.md)

----

## Step 3: Connect the user interface to the shelter API

In this part of the workshop, we want to connect our frontend application to the backend API in order to retrieve 
the list of pets available for adoption, and to submit inquiries to adopt them.
In practice, this boils down to performing HTTP calls 
to [this API][api-spec] **TODO replace with link to the Swagger editor spec viewer, once final**, 
which is exposed at: https://codess-shelter.azurewebsites.net/api/v1/.  

While there are several HTTP third party libraries that can be used in Javascript (e.g. [Request] or [Axios]),
for this workshop, we suggest relying on the native Javascript [fetch] API, which is compatible with 
most browsers in use nowadays.  

 1. To get the list of pets available, we implement an HTTP GET call 
    to `https://codess-shelter.azurewebsites.net/api/v1/pets`, 
    parse the response and set a state variable in the main page of our pet shelter.
    We place this call in the `componentDidMount()` method of our `App` component and use the state attribute to store the
    array of pets data, as [best practice][react-state] for React components.
 2. To submit an inquiry for adoption, we create a [modal form][react-bst-modal] with few fields 
    to be filled out by the inquirer,
    and attach to the `onClick` event of its submit button a function call to the inquiry API.
    In short, every inquiry submission is an HTTP POST call to `https://codess-shelter.azurewebsites.net/api/v1/inquiries`.
    The feedback of that call can be visualized as a simple message at the bottom of the
    modal form using the [conditional rendering][conditional-rend] feature of React.

**Note**: if you are using Typescript, you can avail of its type checking when parsing API 
responses and serializing requests. To do so, you can generate the related interfaces from the
API specifications using a command line tool or simply from the [Swagger Editor][swagger].

<details>
<summary><b>If you need some help with the HTTP calls and the parsing logic, 
click here to read some code snippets.</b></summary><br>

### Retrieving the list of pets from the backend

```javascript
    fetch(`https://codess-shelter.azurewebsites.net/api/v1/pets`)
      .then(response => {
        if (response.status >= 300) {
          throw new Error(`HTTP Error ${response.statusText}`);
        }
        return response.json();
      })
      .then(data => {
        // set data to be a state variable
      });
```

### Submitting the inquiry form

```javascript
   submitInquiry(event: any) {
        event.preventDefault();
        var inquiry = // inquiry details from the state
        fetch(`https://codess-shelter.azurewebsites.net/api/v1/inquiries`, {
            method: "POST",
            mode: "cors",
            headers: {
                "Content-Type": "application/json",
            },
            body: JSON.stringify(inquiry)
        }).then(response => {
            if (response.status !== 201) {
                this.setState({ formState: "error" });
                throw new Error(`HTTP Error ${response.statusText}`);
            }
            return response.json();
        }
        ).then((data: InquiryV1) => {
            this.setState({
                inquiryId: data.id,
                formState: "success"
            });
        })
    }
```
</details>

When you are done, remember to *save* your work with a `git commit` command, as described in the previous steps.
After that, you can continue by adding testing logic, as described [here](./04-testing-your-code.md).


 [api-spec]: https://github.com/codessintheclassroom/api-reference-solution/blob/master/oas3.yaml
 [request]: https://github.com/request/request
 [axios]: https://github.com/axios/axios
 [fetch]: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
 [react-state]: https://reactjs.org/docs/state-and-lifecycle.html
 [react-bst-modal]: https://react-bootstrap.github.io/components/modal/
 [conditional-rend]: https://reactjs.org/docs/conditional-rendering.html#inline-if-else-with-conditional-operator
 [swagger]: https://editor.swagger.io/

----

[⏮ Previous step: Building the UI](./02-building-the-ui.md)&nbsp;|&nbsp;[🏠 Up](./00-index.md)&nbsp;|&nbsp;[⏭ Next step: Testing your code](./04-testing-your-code.md)