<div align="center">
<h1>Page Builder Blocks for Gatsby</h1>
</div>

<p align="center">
Combine the power of <strong>Gatsby</strong>, <strong>MDX</strong> and <strong>Theme UI</strong> to build blazing fast websites.
</p>

<p align="center">
  <a href="https://github.com/arshad/gatsby-themes/blob/master/LICENSE"><img src="https://img.shields.io/npm/l/gatsby-theme-flex.svg" alt="License"></a>
  <a href="https://github.com/arshad/gatsby-themes/pulls"><img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" alt="PRs welcome!" /></a>
  <a href="https://twitter.com/arshadcn"><img src="https://img.shields.io/badge/Follow-%40arshadcn-1da1f2" alt="Follow @arshadcn" /></a>
</p>

<img src="https://arshad.io/uploads/gatsby-theme-flex.gif" />

## About

Flex is a Gatsby theme that ships with pre-built blocks that you can use in your Markdown pages. Then use Theme UI to customize the look and feel of your site.

[See a demo](https://flex.arshad.io)

## Features

- **Customizable** - All blocks can be extended and customized.
- **Extendable** - Build and add your own custom blocks.
- **Accessible** - All blocks are tested for accessiblity.
- **Dark mode** - Support for multiple color modes.
- **SEO** - SEO + Open Graph out of the box.
- **Code Highlighting** - Code highlighting with Prism.

## Quick Start

Create a new Flex site:

```shell
gatsby new site arshad/gatsby-starter-flex
```

Start the development server

```shell
cd site
gatsby develop
```

You should now be able to view your site at `http://localhost:8000`.

## Add a page

Create a page at `content/pages/home/index.mdx` and add the following to it:

```markdown
---
title: Home
excerpt: Welcome to the home page
is_front: TRUE
---
```

This will create a new page and set it as the front page. If you head to `http://localhost:8000`, you should see Home displayed as the page title.

## Add a block

Let's add a hero to the home page. Add the following to `content/pages/home/index.mdx`

```markdown
---
title: Home
excerpt: Welcome to the home page
is_front: TRUE
---

<Hero
heading="Expedita Aperiam"
lead="Sint quaerat et occaecati voluptate illum tenetur."
imageUrl="https://via.placeholder.com/800x450"
style={{
    bg: "muted"
  }}
/>
```

It's that easy.

### Available Blocks

Flex comes with a lot of pre-built blocks that you can use to build your site.

`Cta`, `Div`, `Faqs`, `Feature`, `Hero`, `Logos`, `PageHeader`, `Section`, `Button`, `Card`, `Faq`, `Lead`, `Link`, `Logo`, `Image`, `Testimonial` and many more.

## Theming

Flex makes use of [Theme UI](https://theme-ui.com) under the hood. This makes it very easy to customize and re-use your theme across pages.

### Customize the theme

Create a new file at `src/gatsby-theme-flex/theme.js` and add your custom theme values in there.

Let's change the default primary color.

```js
// src/gatsby-theme-flex/theme.js
export default {
  colors: {
    primary: `#ee00ff`,
  },
}
```

Stop and restart the development server: `gatsby develop`.

## FAQs

We're still working on the documentation. But here's some quick answers to get you started.

### How to customize a block

Use [Component Shadowing](https://www.gatsbyjs.org/docs/themes/shadowing/). Example, to override the `Hero` block, create the following file `src/gatsby-theme-flex/blocks/hero.js` and create your custom `Hero` block.

To customize the `Header`, create the following `src/gatsby-theme-flex/layout/header.js`.

### How to add new props to a block

Shadow the block and add your new props. For example, the following code adds a `foo` prop to the card block:

```js
// src/gatsby-theme-flex/components/card.js
/** @jsx jsx */
import { jsx } from "theme-ui"

export default ({ style, heading, foo, children }) => {
  ...
  {foo}
  ...
}
```

You can now use `foo` in your pages as follows:

```markdown
<Card 
  heading="This is the heading" 
  foo="bar" 
/>
```

### How to add your own block

Shadow the `src/gatsby-theme-flex/blocks.js` component and add the following code:

```js
// src/gatsby-theme-flex/blocks.js
export * from "gatsby-theme-flex/src/blocks"
export { default as MyComponent } from "../my-component.js"
```

```js
// src/my-component.js
/** @jsx jsx */
import { jsx } from "theme-ui"

export default ({ foo }) => <div>{foo}</div>
```

You can now use `MyComponent` in your pages:

```markdown
<MyComponent foo="bar" />
```

## Support

Need help? Create an issue on the main repo [@arshad/gatsby-themes](https://github.com/arshad/gatsby-themes/issues) or ask me [@arshadcn](https://twitter.com/arshadcn).

## License

<a href="https://www.npmjs.com/package/gatsby-theme-flex"><img src="https://img.shields.io/npm/l/gatsby-theme-flex.svg" alt="License"></a>
