# Codess in the classroom

## Web application

### Creation

1. Install the latest long term support (LTS) version of node js from https://nodejs.org/en/. Currently this is version 10. Avoid non LTS versions, e.g. version 11, since they tend to have bugs.
2. Install Visual Studio code from https://code.visualstudio.com/.
3. Create a new folder to store the code, e.g. c:\codess
4. Launch visual studio code and use `File -> Open Folder` to open the codess folder.
5. Open a terminal by clicking on `Terminal -> New Terminal`.
6. Run the following commands

        npx create-react-app web-application --typescript
        cd web-application
        npm start

    This creates a basic typescript based web application and starts it.
    See https://github.com/facebook/create-react-app for more info.

7. Navigate to http://localhost:3000/ to see the running application.

### Adding some UI

1. Run `npm install react-bootstrap @types/react-bootstrap --save` to install the https://react-bootstrap.github.io/ library.
2. Add the bootstrap css file to your index.html file located in web-application/public/index.html

        <link
            rel="stylesheet"
            href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
            integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T"
            crossorigin="anonymous"
        />

3. Use the bootstrap component library to build a basic UI.

    Some useful components to consider:
    
    - Grid layout system: https://react-bootstrap.github.io/layout/grid/
    - Navigation Bar: https://react-bootstrap.github.io/components/navbar/
    - Cards: https://react-bootstrap.github.io/components/cards/
    - Card Layouts: https://react-bootstrap.github.io/components/cards/#card-layout
