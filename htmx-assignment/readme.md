# HTMX - Assignment

We're going to build our own HTMX app, a recipe book. This readme will give you the general guidelines. You should reference the HTMX lesson if you feel lost, as well as the [HTMX documentation](https://htmx.org/), which is very good.

### Setup

Setup is similar to our todo app. You must:

- Run `npm install` to install dependencies.
- Create a database and collection in MongoDB. The collection should be called `recipes`.
- Import the recipes from `models/recipes.json` into your collection.
- Create a `.env` file with a `MONGODB_URI` variable that contains your connection string. Don't forget to add your database name to the end of the connection string, after the `/`.

### Step 1: Displaying Recipes

- Edit the back end route to grab the recipes from the database and render them to the page.

The `forEach` loop written for you in `recipes.ejs` should display the recipes. Reload the page to confirm this works.

### Step 2: Adding About and Contact Pages

- Add GET route handlers for `/recipes`, `/about`, `/contact`. They should each send back _only_ the EJS files for those pages.
- Add HTMX to the front end to load those pages in place when the navbar items are clicked--so put the `hx-` attributes on the correct navbar items. You'll need:
  - `hx-get` to the right route
  - `hx-target` set to `main`
  - `hx-swap` set to `innerHTML` (to replace what's _in_ `main`)
  
**Note**: It might _seem_ helpful to re-use the `/` route handler for when the user clicks the Recipes navbar item, since that route _does_ render the recipes. But that's the route for the _entire_ page, which you do not want in this instance--it's more efficient to just send back the recipes, so only that needs to be re-rendered.

### Step 3: A Single Recipe View

- Add a route handler for `/recipe/:id` that sends back an EJS file for a single recipe. (You'll have to make this file.)
- Add HTMX to the front end to load that page in place when a recipe is clicked. You'll need:
  - `hx-get` to the right route
  - `hx-target` to `main`
  - `hx-swap` set to `innerHTML` (to replace what's _in_ `main`)
- The single-recipe EJS file you make should display the recipe's name, ingredients, and steps. It should also ideally have a back button to return to the main page, but, if not, the user can click the navbar item.

### Bonus

For the below, remember to update in place using HTMX, _not_ sending the user to a new page!

- We're only rendering recipes for now. In recommended order, add:
  - Deleting recipes.
  - Editing recipes.
  - Adding recipes.

When doing so, don't forget that the ingredients and steps properties are arrays. You can take them in as a comma-separated list in an input box and convert to an array. `array.join` and `string.split` are helpful here!

For adding and editing recipes, give the user separate input boxes for each ingredient/step. We recommend a button at the bottom that adds a new input box.
