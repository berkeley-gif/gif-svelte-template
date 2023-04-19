# GIF Svelte Template

This repo serves as a reference for setting up new GIF projects using [SvelteKit](https://kit.svelte.dev/) with 2 different Svelete component libraries:

- [Carbon Components Svelte](https://carbon-components-svelte.onrender.com/)
- [Svelte Material UI](https://sveltematerialui.com/).

The repo includes best practices for linting styles, github workflows and git hooks. It's been tested with SvelteKit version 1.5.0, svelte version 3.54, vite version 4.2.0 and node version 18.

**Note: This template should be updated as the tooling and best practicies evolve.**

**Note: It's suggested that you follow the steps provided below to initiate a new project instead of duplicating this repository. This will allow you to gain a better understanding of how everything is connected.**

## Check your Node version

This project uses Node 16 and above. Run the following command before installing or running your development environment:

```
nvm use 16
```

## Create a new GIF SvelteKit project

The best way to create a new SvelteKit project is by following the instructions on [Creating a Project](https://kit.svelte.dev/docs/creating-a-project) in [SvelteKit documentation](https://kit.svelte.dev/docs/introduction). That way you get the latest npm packages. Everything you need to build a Svelte project is powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte).

```bash
# create a new project in the current directory
npm create svelte@latest

# create a new project in my-app
npm create svelte@latest my-app

# install packages listed by SvelteKit
npm install

# install sass
npm i -D sass
```

## Using component libraries

### Using Carbon Components Svelte

This repo contains a basic example of using [Carbon Components Svelte](https://carbon-components-svelte.onrender.com/). These components use the [Carbon Design System v11](https://www.carbondesignsystem.com/) developed by IBM. The Cal-Adapt 2.0 website is developed using an older version of the Carbon Components Svelte that use Carbon Design System v10.

```bash
npm i -D carbon-components-svelte

# OPTIONAL PACKAGES

# carbon-components is required if you are going
# to style the carbon components with SCSS
npm i -D carbon-components

# icons
npm i -D carbon-icons-svelte

# @carbon/charts-svelte  is a collection of simple and complex charts
# https://carbondesignsystem.com/data-visualization/getting-started/
# https://charts.carbondesignsystem.com/svelte/?path=/story/intro--welcome
npm i -D @carbon/charts-svelte
```

### Using Material UI Components for Svelte

This repo contains a basic example of using the Svelte Material UI components. For more detailed instructions see the [Svelte Material UI](https://sveltematerialui.com/SVELTEKIT.md) documentation.

```bash
npm i -D @smui/button
npm i -D @smui/card

npm i -D smui-theme
```

## Setup Github workflows

- Create a .github/workflows directory in the root of your repository.
- Create a new `node.js.yml` file inside the workflows directory. This file will define your workflow and the actions that should be taken when specific events occur (e.g. push to main branch).
- Define your workflow using the YAML syntax. You can specify multiple jobs and steps for each job.
- Add and commit the YAML file to your repository.
- GitHub will automatically run your workflow when the specified events occur.

For an example of github workflow see the `src/.github/workflows/node.js.yml` file in this repo. More about Github actions on https://help.github.com/actions/language-and-framework-guides/using-nodejs-with-github-actions

## Set up Git hooks

Git hooks are scripts that run automatically when certain events occur in your Git workflow, such as committing or pushing changes. These are useful for linting files and running tests.

Running git hooks against whole codebase is slow. Currently the repo implemets linting of files on staging only. Linting for staged files is setup using [Husky](https://typicode.github.io/husky/#/) and [lint-staged](https://github.com/okonet/lint-staged) packages.

```bash
# This will install husky and lint-staged, then add a configuration to the project’s
# package.json that will automatically format supported files in a pre-commit hook.
# see https://prettier.io/docs/en/precommit.html
npx mrm@2 lint-staged

# packages for linting & formatting js/ts & html files (eslint and prettier)
# are already installed by SvelteKit

# install packages for linting styles
npm i -D stylelint stylelint-config-prettier-scss stylelint-config-html stylelint-config-carbon

# you might need to use --force with the comman above if the stylelint dependencies between
# packages are out of sync

```

Update the `lint` and `format` scripts & add a new `lint_style` script in `package.json` file:

```
		"lint": "prettier --plugin-search-dir . --check . && eslint . --cache --fix",
		"lint:styles": "stylelint \"**/*.{css,scss,sass,svelte}\" --cache --ignore-path .gitignore --fix --allow-empty-input",
		"format": "prettier --plugin-search-dir . --write .",
```

Update the `lint-staged` configuration in the `package.json` file to run the scripts defined above:

```
  "lint-staged": {
		"*.{js,ts,svelte}": "npm run lint",
		"*.{css,scss,svelte}": "npm run lint:styles",
		"*.{js,svelte,jsx,ts,tsx,md,html,css,scss}": "npm run format"
  }
```

Create a new `.stylelintrc.json` configuration file in your repo. See `.stylelintrc.json` in this repo for useful stylelint rules.

Update the `prepare` task in `package.json` to.

```
  "prepare": "svelte-kit sync && husky install"
```

Sometimes if you add extra spaces or change a bracket position and run lint-staged and try to commit the changed file, git complains about an empty git commit (because technically there's no change in the codebase). To allow empty commits, update the pre-commit hook for running lint-staged `.husky/pre-commit` to:

```bash
npx lint-staged --allow-empty

```

## Testing

End to end tests are written using [Playwright]() and unit tests are writtin using [vitest]().

```bash
npm i -D vitest

    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/svelte": "^3.2.2",
    "@testing-library/user-event": "^14.4.3",
```

Create a new `.stylelintrc.json` configuration file in your repo. See `.stylelintrc.json` in this repo for useful stylelint rules. Commit the file to your repo.

Add a new task to the the `package.json` file.

```
  "test:unit": "vitest"
```

```
  test: {
    include: ["src/**/*.{test,spec}.{js,ts}"],
    globals: true,
    environment: "jsdom",
    setupFiles: "./tests/setup.ts",
    types: ["vitest/globals"]
  },
```

## Developing

Start a development server:

```bash
# vite starts a development server at port 5173
npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

If you want to use a different port and open the app in a new browser tab, add the following `start` script to `package.json`.

```bash
  "start": "npm run dev  -- --open --port 3000",
```

## Building

To create a production version of your app:

```bash
npm run build
```

You can preview the production build with `npm run preview`.

## Credits

- Template created using [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte) by @cohenlea
- Settings for Github workflows and actions taken from https://github.com/berkeley-gif/cal-adapt-svelte-components and https://github.com/berkeley-gif/caladapt-website-2021 developed by @clhenrick.
- Documentation on theming Carbon Svelte Components and setting up a new GIF SvelteKit project added by @mukhtyar
