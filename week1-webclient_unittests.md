# Codess in the Classroom - Week 1: The Web Client

## Adding unit tests for your pet component.

At this stage you should already have a pet component created in the src folder. It's valuable to now develop test for this component so:
1. The correctness of the current implementation is validated.
2. That any future changes do not break functionality you have already developed.

Test driven development (TDD) is also popular with some developers. With TDD a developer would write the tests as specifications upfront and only implement enough code to make the tests pass.

### Step by step instructions for adding unit tests.

This set of instructions are using [jest-dom](https://github.com/testing-library/jest-dom) and the [react-testing-library](https://github.com/testing-library/react-testing-library) to help write tests. There are many libraries availble to make writing tests easier, but for this class we have picked these two.

1. Install jest-dom and the react-testing-library using this command

       npm install jest-dom react-testing-library --save-dev

2. Add a new file called PetCard.test.tsx. It's important for this file to end in test.tsx because this is how the build system knows that it is a test file and includes it in test runs.

3. Add imports to the top of the file to reference

    - the two libraries installed in step 1
    - the render helper from the react-testing-library which is used to render the component for testing
    - react which is required to render any component.

            import 'react-testing-library/cleanup-after-each';
            import 'jest-dom/extend-expect';
            import { render } from 'react-testing-library';

            import * as React from 'react';

4. Add an import statement to import the PetCard component that we are going to test. Make sure that the path references the location of the PetCard.tsx file if your PetCard.test.tsx is not in the same folder as PetCard.tsx.

        import { PetCard } from './PetCard';

5. Add an import statement to import the Pet data model that is passed to the PetCard as a parameter. Again make sure that the path matches the location where the model is located relative to the Petcard.test.tsx file.

        import { PetV1 } from './model/petV1';

6. Add a variable to contain the parameters needed to render a PetCard.

        const petMock: PetV1 = {
            "id": "225c5957d7f450baec75a67ede427e9",
            "name": "Fido",
            "status": "available",
            "kind": "dog",
            "breed": "Labrador",
            "description": "Fido is a good boy who loves long walks in the park, playing with his ball and licking faces. He's great with children and an absolute sweetheart.",
            "birthday": "2016-04-15",
            "photos": ["https://upload.wikimedia.org/wikipedia/commons/b/b3/Labrador_on_Quantock_%282307909488%29.jpg"]
        };

7. Add `describe` and `it` functions for your first test.

        describe('PetCard', () => {
            it('should render the given name', () => {
                const { getByText } = render(<PetCard pet={petMock}/>);
                expect(getByText('Fido')).toBeInTheDocument();
            });
        });

    - The first parameter passed to `describe` should be the name of the component that is being tested.
    - The first parameter passed to `it` should describe in natural language (e.g. English) what expectation you are trying to test.
    - The second parameters passed to `describe` and `it` are callbacks executed by the testing framework that should contain the actual testing code.
    - The line `const { getByText } = render(<PetCard pet={petMock}/>);` renders the PetCard using the mock data defined in 6 above, and returns a function `getByText` that allows you to check whether certain text values exist in the rendered component.
    - The line `expect(getByText('Fido')).toBeInTheDocument();` defines an expectation that the text `Fido` should be in the rendered component.

8. There are many different ways in which the rendered component and its parts can be checked for validity.

    - There are many ways in which sub parts of the component can be discovered in addition to `getByText` used above. See the [dom-testing-library cheatsheet](https://testing-library.com/docs/dom-testing-library/cheatsheet#queries) for a list.
    - There are also many ways in which checks can be done on these discovered sub parts in addition to `toBeInTheDocument` used above. There are checks to do anything from whether an attribute exists on a dom element to whether an element is visible or not. See the [jest-dom documentation](https://www.npmjs.com/package/jest-dom#custom-matchers) for more examples.

9. See if you can add additional tests for the following expectations:

        PetCard should render the given description
        PetCard should render the adopt button

10. See the bottom of this page for an end to end solution containing one possible way to write these.

### Running the tests.

To run the tests execute the following in a terminal:

    npm run test

This will start a process that runs continuously. The process will recompile the code if anything changes and is saved, and also re-run the tests at that time. The results that are printed out looks similar to this when all the tests succeeded:

    Test Suites: 2 passed, 2 total
    Tests:       4 passed, 4 total

Each seperate test file is considered a test suite and each `it` is counted a single test.

Test failures are printed out on the console as well, e.g:

    Test Suites: 1 failed, 1 passed, 2 total
    Tests:       1 failed, 3 passed, 4 total

To simulate a failure, try changing the unit test described above, so that the text that is expected is `Spot` instead of `Fido`, e.g:

    expect(getByText('Spot')).toBeInTheDocument();

This will print out detailed information about the test that failed including the expectation that wasn't met.

### Best practices when writing tests.

The description that you give your tests should be similar to a specification. A good template to consider is `Code a should do action b in case of c`. The code in the test should do checks that match the description. Since requirements tend to change over time or even get lost, unit tests can serve as an accurate and up to date specification of the expected behavior of the application. Since they are checked in with the code, they are easier to keep in sync with the code and maintain than purely textual specifications.

### Full sample solution.

<details>
<summary>Click here to reveal the full sample solution.</summary>

    import 'react-testing-library/cleanup-after-each';
    import 'jest-dom/extend-expect';

    import * as React from 'react';

    import { PetCard } from './PetCard';
    import { render } from 'react-testing-library';
    import { PetV1 } from './model/petV1';

    const petMock : PetV1 = {
        "id": "225c5957d7f450baec75a67ede427e9",
        "name": "Fido",
        "status": "available",
        "kind": "dog",
        "breed": "Labrador",
        "description": "Fido is a good boy who loves long walks in the park, playing with his ball and licking faces. He's great with children and an absolute sweetheart.",
        "birthday": "2016-04-15",
        "photos": ["https://upload.wikimedia.org/wikipedia/commons/b/b3/Labrador_on_Quantock_%282307909488%29.jpg"]
    };

    describe('PetCard', () => {
        it('should render the given name', () => {
            const { getByText } = render(<PetCard pet={petMock}/>);
            expect(getByText('Fido')).toBeInTheDocument();
        });

        it('should render the given description', () => {
            const { getByText } = render(<PetCard pet={petMock}/>);
            expect(getByText(petMock.description!)).toBeInTheDocument();
        });

        it('should render the adopt button', () => {
            const { getByText } = render(<PetCard pet={petMock}/>);
            expect(getByText('Adopt')).toBeInTheDocument();
        });
    });

<details>