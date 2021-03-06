# Quicksheets

A simple browser-based spreadsheet app: https://sheets.habbes.xyz

![Quicksheets screencast](screencast.gif)

## How it works

When a cell on the spreadsheet is updated, all the non-empty cells
are parsed and evaluated and updated with their new values (or errors). It has plenty of room for optimization but should be good enough for a sparse 50x26 grid.

To enter a formula in a cell, prefix the formula expression with `=`, e.g. `=SUM(A1:A10)`.

### Code organisation

- `src`
    - `app`: contains all the UI code, based on React and Redux
    - `lib`: contains the modules implementing the core spreadsheet engine
        - `eval`: modules responsible for parsing and evaluating formulae and expressions
        - `functions`: implementations of the functions available in the spreadsheet (e.g. SUM, PRODUCT, etc.)
        - `grid`: abstractions for working with 2-D grids
        - `spreadsheet.js`: implements the `Spreadsheet` class that encapsulate the entire spreadsheet engine

The formula syntax is specified in [grammar.md](grammar.md).

All available built-in functions are listed in [functions.md](functions.md)

Unit tests are located in `tests` folders in the various subfolders under the `src` directory.
E2E tests are located in `cypress/integration` directory.

## Available Scripts

In the project directory, you can run:

- `yarn start`

Runs the app in the development mode.<br>
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

The page will reload if you make edits.<br>
You will also see any lint errors in the console.

- `yarn test`

Runs unit tests in interactive mode. Tests are re-run when files are changed.

- `yarn test:e2e`

Runs end-to-end tests (using Cypress)

- `yarn test:e2e-watch`

Allows you to run end-to-end tests interactively and watch them on a GUI.

- `yarn test:all`

Runs all the tests

- `yarn build`

Builds the app for production to the `build` folder.

- `yarn deploy`

Builds and deploys the app to Firebase hosting.

