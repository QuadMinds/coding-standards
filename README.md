# Quadminds Technologies - Codign Standards 
Quadminds Coding Standards is a collaborative repo of code guidelines with some of the team's conventions.

## Table of Contents

1. [Introduction](#introduction)
2. [Why Coding Standards?](#why-coding-standards?)
3. [Naming](#naming)
4. [ESLint](#eslint)
   1. [Casing](#casing)
   2. [File names](#file-names)
5. [Coding](#coding)
6. [Formatting](#formatting)
7. [Comments](#comments)
8. [TypeScript](#typescript)
9. [GIT](#git)
   1. [Branches](#branches)
   2. [Commit messages](#commit-messages)
   3. [Code Reviews](#code-reviews)
10. [Node.js](#node.js)
11. [Recommended Frameworks](#recommended-frameworks)
   1. [React](#react)
12. [Recommended Libraries](#recommended-libraries)
13. [Definition of Done Checklist](#definition-of-done-checklist)
14. [Development environment](#development-environment)
    1. [VSCode](#vscode)
    2. [WebStorm](#webstorm)

## Introduction 
The **SaaS** repository is composed with a combination of both vanilla **PHP** and libs based on the latter.  

While some of these guidelines could be applied to new features developed in, the main purpose of this document is to serve as a follow up guide for projects built in newer technologies, such as the **Cloud Flash** repository and **Node.js** based applications.  

## Why Coding Standards?

A coding standard gives a uniform appearance to the codes written by different members of a team.
- It improves readability, and maintainability of the code and it reduces complexity also.
- It helps in code reuse and helps to detect error easily.
- It promotes sound programming practices and increases efficiency of the programmers.

## Naming

Choosing good names is critical to creating code that is easy to use and easy to understand. You
should always take the time to think about whether you have chosen the right name for something,
especially if it is part of the public API.

#### English

All new code made, including names, comments, etc. must be in English.

> Tip: install a spell checker in your IDE to avoid typos.
> [VSCode](#recommended-extensions-for-vscode) or [WebStorm](#recommended-plugins-for-webstorm)

#### Use one name for one thing

Always use the same name for the same thing. So use the same name within the JavaScript, CSS and HTML for the same thing. Align
naming with the whole team: Backend, Frontend, UX, Design, PM, client, etc.

For big projects with their own jargon it could help to create a dictionary.

#### Descriptive

Names must be descriptive for the working or usage of the class, method or variable.

###### The name should always end with what the object is.

For example: a button must always end with `Button`.

- `MenuButton` a button used in the menu
- `CardHeader` the header of a card
- `DialogContentText` a text in the content body of a dialog

There is no limit for the length of a name, so prefer a long name which is clear and descriptive
than a short name which is not clear.

#### Context

A name should make sense within its context and should not have unnecessary information for that
context. For example a variable that holds the name of a user can be named `name` within a `User`
context. However if you need to hold the name of a user in another place, `userName` might be a
better name. Adding `user` within a `User` context (`user.userName`) is redundant and should be
avoided.

#### Abbreviations

Avoid them as a general rule. For example, `calculateOptimalValue()` is a better method name than
`calcOptVal()`. Being clear is more important than minimizing keystrokes. 

A few abbreviations that are allowed to use:

- `app` for application
- `args` for arguments
- `auto` for automatic, as in `autoLayout`
- `bin` for binary
- `id` for identifier. Please note that 'd' should be written in lowercase when used in combination
  with another word, like `userId`.
- `info` for information, as in `GridRowInfo`
- `init` for initialize
- `lib` for library
- `max` for maximum, as in `maxHeight`
- `min` for minimum, as in `minWidth`
- `param` or `params` for parameter or parameters respectively
- `prop` or `props` for property or properties respectively
- `ref` for reference
- `temp` for temporary
- `ui` for user interface
- `util` or `utils` for utility or utilities

#### Plural or singular?

##### Classes, Interfaces, Types and Enums

Should always have a **singular** name, unless the object is only used to hold other values and
these other value are more important then the object itself, like `Props`, `Settings` or `Options`.
For example: `MyComponentProps`, `ProductionSettings` or `CalendarOptions`.

##### Arrays

Or other kind of lists should have a plural name or end with `List` or `Collection`, like
`userList`.

##### Folders

If a folder holds multiple files, but all related to one main type, it should have a singular name.
If it holds multiple main files of a type, it should have a plural name.

For example, the folder `page` contains a single page, with maybe some helper files. The folder
`pages` contains multiple pages.

#### Functions

Prefer using a verb as a name to indicate it will do something. Like `render`, `open` or `getData`.

#### Classes, variables, properties, etc.

All non-functions should have a noun as a name, not a verb.

#### Booleans

Should start with `is`, `has`, `will` or `should`. Like `isValid` or `hasValues`.

#### Always Affirmative

Avoid negations. _“Don’t ever not avoid negative logic”_. Prefer `isShown` over `isHidden` or
`isEnabled` over `isDisabled`. Do not use names like `notEditable`.

#### TypeScript Generics

If the usages of the generic is obvious, then naming that generic `T` is sufficient. As long as the
usage is clear you can use `U`, `V` etc. for any following generic.

If the usage is not obvious, you should use a more descriptive name. The same naming rules as for
classes will apply then.

### Casing ✴
This one depends on the project beign work in. Follow the guidelenss for **Javascript** apps and completely new features developed on **Cloud Flash**.

If the feature you are working on is on a **legacy** file, keep the codign style wether it makes sense. 

However you should always try to avoid adding new functionality to existing files if the code style is completely different from the conventional one. Instead, create new files following the standard and reference them in older ones if needed.

#### Classes, Interfaces, Types and Generics

**PascalCase** Every individual word start with an upper case character, no underscores, no dashes.

#### Functions, properties, arguments and variables

**camelCase** Starts with a lower case character, every following individual word start with a upper
case character, no underscores, no dashes.

#### Globally used constants

**SNAKE_UPPER_CASE** Only use upper case characters, individual words must be separated with an
underscore.

#### CSS Class names

**kebab-case** Only use lower case characters, individual words must be separated with a dash.

#### Abbreviations and Acronyms

Abbreviations and acronyms should be treated as words, which means only the first character will be
capitalized for camelCase and PascalCase.

```ts
const jsonApiSdkUrl = new JsonApiSdkUrl();
```

### File names [WIP]

If a file contains only one class, type or object, or when there is one main class, type or object
with some helper classes, types or objects, the file should have the same name, in the same casing,
as that (main) class, type or object. 

## Coding 👨‍🚀🐱‍🏍

Every function or class should do **one thing** (and do it good). If it needs to do more than one
thing, split it up. Keep your files, classes and functions small. It’s okay to have a file with just
a single line.

#### Pure functions

Prefer writing pure functions, which means they do not manipulate the input arguments or
reference/manipulate global state. This makes your code better scalable and testable.

#### Separate Logic From Configuration

Write code that is reusable, scalable and testable.

#### Do not repeat yourself (DRY)

- Do not copy code to another place.
- Avoid using the same string twice in a project.
- Move shared logic to a shared place.
- Make sure you do not have to adapt changes in multiple places.

#### Default in a switch

Every `switch` must have a `default`. If there is no need to handle the `default`, either throw an
`Error` or add a comment that the default is explicitly ignored.

```js
switch (state) {
  case 1: {
    // ....
    break;
  }
  case 2: {
    // ....
    break;
  }
  default: {
    throw new Error(`Unhandled value for state '${state}'`);
  }
}
```

_throw an error for things that should not occur_

```js
switch (state) {
  case 1: {
    // ....
    break;
  }
  case 2: {
    // ....
    break;
  }
  default: {
    // do nothing
    break;
  }
}
```

_add a comment that the default is explicit ignored_

Adding the comment makes it clear the developer did not forget to implement the default.

## Formatting ✨

All code within a project should have the same formatting. To enforce that we use
[Prettier](https://prettier.io/).

## Comments

#### Documentation comments

If you're new to a project or piece of code, when going over it, and trying to understand it, add
explanatory comments on things that took you some time to figure out.

If someone else asks during a code review why something is done a certain way, see if you can answer
it with a code comment instead of a reply in the review tool (when applicable).

#### Regular Expressions

Since regular expressions can be hard to read, they should have a comment that indicate what they
do. Especially when they are complex.

#### Commented out code

Don't leave commented out code into project. You can always find it back in the version control
system. If for some reason you want to keep commented out code in the project, add a comment
explaining why it is commented out.

#### TODO

If something needs to be changed or refactored later, add a `// TODO ` comment to indicate what the
issue is.

#### Refactoring

If you refactor code that has comments, please check afterwards if the comments still make sense or
need to be updated.

#### Access Modifiers

Keep your code as strict as possible, so keep all functions and properties `private` unless they
have to be `protected` or `public`.

#### Readonly

In order to be as strict as possible, every property should be set to readonly unless it should be
writable.

#### Arrays

Always prefer `ReadonlyArray` over a regular `Array` unless it must be possible to modify the Array.

## GIT

### Branches

We use [GitFlow](https://datasift.github.io/gitflow/IntroducingGitFlow.html) for our branching
strategy.

Branch names should adhere to the following structure:

- `bugfix` or `feature` + `/` + `{TICKET_KEY}-{TICKET_TITLE}` e.g.
  `bugfix/AB-1234-accessibility-homepage-contrast`

#### Automatic deployment of branches

Some projects will automatically deploy to an environment when pushing commits into a specific
branch. Which branch is connected to which environment should be written in the `README.md` of the
project.

### Commit messages

- Make sure it is always clear why a change was made.
- Only commit one feature at the time.
- Always check your commit in details to avoid committing wrong code.

### Code Reviews

Always let someone else review your code in the Pull/Merge Request. Make sure all code review
comments are resolved, before you merge it!

## Node.js

### nvm

When setting up **Node.js** on a new machine, it is strongly recommended to use a versioning tool such
as [nvm](https://github.com/nvm-sh/nvm). There are often times when we must switch between versions
for testing or for certain features. Tools such as [nvm](https://github.com/nvm-sh/nvm) make this
easy and simple.

### Long-term support

You **must** always use the **LTS** (Long-term support) version of Node.js as it is considered
stable and will ensure that you don't encounter any unexpected issues. Furthermore, when creating a
new project or tool, it **must** always target the **LTS** version, unless there is a good reason
not to e.g. an experimental tool or long-term project. To find out the current LTS version, you can
use a tool such as [nvm](https://github.com/nvm-sh/nvm) or simply check the Node.js
[website](https://nodejs.org/en/download).

## Recommended Frameworks [WIP]

### Frontend - React

We recommend using [React](https://reactjs.org/) for large Single Page Applications (SPA's). React
is suited for long term projects that need stable and maintainable code. React works great together
with [TypeScript](https://www.typescriptlang.org/).

### Backend - Nest 

We recommend using [Nest](https://reactjs.org/) for building efficient, reliable and scalable server-side applications. Nest
is suited for long term projects that need stable and maintainable code. Nest uses by default [TypeScript](https://www.typescriptlang.org/).

## Recommended libs [WIP]

#### Coding

- [axios](https://github.com/axios/axios) - Promise based HTTP client
- [date-fns](https://www.npmjs.com/package/date-fns) - provides the most comprehensive, yet simple
  and consistent toolset for manipulating JavaScript dates
- [i18next](https://www.npmjs.com/package/i18next) - Internationalization library
- [Yup](https://github.com/jquense/yup) - Form validation

#### TypeScript

- [isntnt](https://www.npmjs.com/package/isntnt) - Composable TypeScript predicate
- [ts-essentials](https://www.npmjs.com/package/ts-essentials) - TypeScript utilities

#### React

- [Formik](https://jaredpalmer.com/formik/) - Forms
- [React Router](https://reacttraining.com/react-router/) - Router library for React
- [react-i18next](https://react.i18next.com/) - Internationalization library for React
- [react-intl](https://www.npmjs.com/package/react-intl) - Internationalization library for React

##### Redux

- [Redux](https://redux.js.org/) - A Predictable State Container for JS Apps

#### PHP [WIP]

#### Development [WIP]


## Definition of Done Checklist

#### Before Starting feature

- [x] Read the ticket. If no ticket is present, create one yourself or ask the Project Manager to
      create one.
- [x] Make sure the ticket is clear and actionable. If not, reassign the ticket to the person
      responsible for the creation of the tickets (the project manager or project lead) until the
      ticket is 100% clear.
- [x] Create a feature branch (`feature/ticket-number-feature-name` or for Jira use the default
      branch name when creating a branch from a ticket).

#### General Tasks

- [x] Double check if feature is properly working on all browsers specified in the browser matrix.
- [x] Double check if feature is properly working on all resolutions.
- [x] Review all commits and check if there is room for improvement.
- [x] Could any of the functions you wrote be reused in other components/features? If so, rewrite it
      and restart the checklist process.
- [x] Ask yourself in which scenarios could this fail?
- [x] Make sure to check that you are handling possible error cases.
- [x] Merge latest develop into branch and see if there are no conflicts. If there are conflicts
      please ask for help if you don't know which part of the code should stay.
- [x] Remove unnecessary comments.
- [x] Check the name and semantics of all functions, properties, variables etc. Do they still make
      sense? Could someone that doesn't know the code understand what it is doing?
- [x] Read your code again. Do you think it can be done better or optimized? Do it. Start process
      again.
- [x] Read the description of the ticket / email again. Did you really do what is asked for? Does
      your change solve the issue?
- [x] Run build tasks and see if they work.
- [x] Does your project have code that isn't used anymore? Throw it away!
- [x] Make sure all linting is passing.

#### UI Task

- [x] Check that
      [HTML5 Semantic Elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#content_sectioning)
      are used appropriately (`header`, `section`, `footer`, `main`...).
- [x] All images have an `alt` property
- [x] All `<a>` have `title` property
- [x] Check if all images are optimized (Saved for web and compressed, resized accordingly)
- [x] Headings (`h1`, `h2`, `h3`...) are used in the correct order.
- [x] All `input`'s have a `label`
- [x] Check if you can navigate the website with keyboard (using tabs)
- [x] Check if all videos are compressed correctly
- [x] Add `aria` labels.
- [x] Check if the fonts are being loaded properly.
- [x] Check if images are being lazy loaded and for proper usage of picture with responsive images
- [x] Check the `hover`, `disabled`, `invalid` and `error` states on buttons, links, form elements,
      etc.

#### Before every release

- [x] Check for proper html `doctype`.
- [x] Check for proper `viewport` tags.
- [x] Check the site has a `title` tag.
- [x] Check for Social sharing `meta` tags.
- [x] Check the site `description`.
- [x] Check the site again while throttling the internet connection. Does it still work? Do you have
      loaders in place?
- [x] What happens if you press the `back` button in the browser? And then the `forward` button?
- [x] What happens if you refresh the page halfway the flow?
- [x] What happens if you directly enter a page at the end of the flow?
- [x] What happens if you navigate away during an async process?
- [x] What happens if you manually change a value in the URL?
- [x] Is there a `404`?
- [x] Check for a favicon.
- [x] Check for JavaScript errors in the console.
- [x] Remove all console.logs.

#### Deployment process

- [x] QA/Staging/UAT/Dev deployments before every Production release are a **must**. No matter if
      it's a hotfix or if the PM is pushing. Unless everything is broken, please follow the rules.
- [x] No Friday deploys. Inform your project manager not to rely on Friday deployments 😀
- [x] Run the website through page insights /
      [Google Lighthouse](https://developers.google.com/web/tools/lighthouse/). (Run audits in
      chrome)

## Development environment

### VSCode

Free code editor made by Microsoft. https://code.visualstudio.com/

#### Recommended extensions for VSCode

Code linting / formatting:

- [prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
- [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker)
- [eslint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
- [stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)

Styling Framework:

- [vscode-styled-components](https://marketplace.visualstudio.com/items?itemName=jpoissonnier.vscode-styled-components)

Collaborating:

- [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- [Live Share](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsliveshare)
- [Jira and Bitbucket (Official)](https://marketplace.visualstudio.com/items?itemName=Atlassian.atlascode)

JS/TS Framework:

- [Vetur (.vue)](https://marketplace.visualstudio.com/items?itemName=octref.vetur)
- [Angular Schematics](https://marketplace.visualstudio.com/items?itemName=cyrilletuzi.angular-schematics)
- [Angular Language Service](https://marketplace.visualstudio.com/items?itemName=Angular.ng-template)
- [React Snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)

Miscellaneous:

- [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
- [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client)

#### Recommended settings for VSCode

User settings.json:

```json
{
  "editor.formatOnSave": true,
  "editor.renderWhitespace": "all",
  "editor.rulers": [100],
  "files.eol": "\n",
  "files.trimTrailingWhitespace": true,
  "html.format.indentHandlebars": true,
  "html.format.wrapAttributes": "force-expand-multiline",
  "javascript.preferences.importModuleSpecifier": "relative",
  "typescript.preferences.importModuleSpecifier": "relative"
}
```

### WebStorm

Integrated development environment focussed on web development made by JetBrains.
https://www.jetbrains.com/webstorm/

#### Recommended plugins for WebStorm

- [Spellchecking](https://www.jetbrains.com/help/webstorm/spellchecking.html)
- [String Manipulation](https://plugins.jetbrains.com/plugin/2162-string-manipulation)
- [CamelCase](https://plugins.jetbrains.com/plugin/7160-camelcase)
