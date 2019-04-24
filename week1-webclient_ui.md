# Codess in the Classroom - Week 1: The Web Client

### Building the Pet Shelter UI

There are several UI frameworks that can be used to have a good looking UI with React without
the need of writing cascading style sheets (CSS) files.
For instance, one can use [Bootstrap][bootstrap], [Material-UI][material-ui] or [Office UI Fabric][office-ui-fabric].  
For this project, we chose to use Bootstrap, with its most popular React bindings: [react-boostrap][react-bootstrap].

1. Run `npm install react-bootstrap @types/react-bootstrap` to install the [react-boostrap][react-bootstrap] library.
2. Add the bootstrap css file to your HTML index file located in `public/index.html`

        <link
            rel="stylesheet"
            href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
            integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T"
            crossorigin="anonymous"
        />

3. Use the bootstrap component library to build a basic UI

    Some useful components to consider:
    
    - Grid layout system: https://react-bootstrap.github.io/layout/grid/
    - Navigation Bar: https://react-bootstrap.github.io/components/navbar/
    - Cards: https://react-bootstrap.github.io/components/cards/
    - Card Layouts: https://react-bootstrap.github.io/components/cards/#card-layout

    <details>
    <summary><b>Click here to have further hints on how to construct the UI</b></summary><br>
        1. add `Container`, `Row` and `Col` components to the `render()` method of the App component
        2. call batman
        3. etc   
    
    </details>


 [bootstrap]: https://getbootstrap.com/
 [react-bootstrap]: https://react-bootstrap.github.io/
 [material-ui]: https://material-ui.com/
 [office-ui-fabric]: https://developer.microsoft.com/en-us/fabric