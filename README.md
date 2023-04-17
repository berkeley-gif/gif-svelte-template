# GIF Svelte Template

This repo serves as a reference for setting up new GIF projects using Svelte, [SvelteKit](https://kit.svelte.dev/) and [Carbon Components Svelte](https://carbon-components-svelte.onrender.com/). The repo includes best practices for linting styles, github workflows and git hooks. It's been tested with SvelteKit version 1.5.0, svelte version 3.54, vite version 4.2.0 and node version 18.

**Note:** This template should be updated as the tooling and best practicies evolve.

**Note:** It's suggested that you follow the steps provided below to initiate a new project instead of duplicating this repository. This will allow you to gain a better understanding of how everything is connected.

## Check your Node version

This project uses Node 16 and above. Run the following command before installing or running your development environment:

```
nvm use 16
```

## Create a new GIF project

The best way to create a new SvelteKit project is by following the instructions on [Creating a Project](https://kit.svelte.dev/docs/creating-a-project) in [SvelteKit documentation](https://kit.svelte.dev/docs/introduction). That way you get the latest npm packages. Everything you need to build a Svelte project is powered by [`create-svelte`](https://github.com/sveltejs/kit/tree/master/packages/create-svelte).

```bash
# create a new project in the current directory
npm create svelte@latest

# create a new project in my-app
npm create svelte@latest my-app
```

## Install packages reccomended by SvelteKit and packages specific to the GIF stack

Once you've created a project and installed dependencies with `npm install` install the following packages specific to the GIF stack.

```bash
npm i -D sass
npm i -D carbon-components-svelte
npm i -D carbon-icons-svelte

# the following packags are optional

# carbon-component is required if you are going
# to style the Svelte carbon components with SCSS
# see the Styles for more details
npm i -D carbon-components

# charts
npm i -D @carbon/charts-svelte
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
# install Husky and lint-staged as a dev dependency
npm i -D husky lint-staged
# enable Git hooks
npx husky install

# packages for linting js/ts & html files are already installed by SvelteKit
# (eslint and prettier)

# install packages for linting styles
npm i -D stylelint stylelint-config-prettier-scss stylelint-config-html stylelint-config-carbon --force

```

Add a `lint-staged` configuration to the `package.json` file.

```
  "lint-staged": {
    "*.{js,ts,svelte}": "eslint --cache",
    "*.{css,scss,svelte}": "stylelint --allow-empty-input",
    "*.{js,svelte,jsx,ts,tsx,md,html,css,scss}": "prettier --write"
  }
```

Create a new `.stylelintrc.json` configuration file in your repo. See `.stylelintrc.json` in this repo for useful stylelint rules. Commit the file to your repo.

Add a new task to the the `package.json` file.

```
  "prepare": "svelte-kit sync && husky install"
```

Add a pre-commit hook for running linting for staged files. Commit the new file `.husky/pre-commit` created to your repo.

```bash
npx husky add .husky/pre-commit 'npx lint-staged'

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

Best practices settings taken from https://github.com/berkeley-gif/cal-adapt-svelte-components and https://github.com/berkeley-gif/caladapt-website-2021 developed by Chris Hendricks.
