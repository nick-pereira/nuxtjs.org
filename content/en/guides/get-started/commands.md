---
title: Commands and Deployment
description: Nuxt.js comes with a set of useful commands, both for development and production purpose.
position: 4
category: get-started
---

Nuxt.js comes with a set of useful commands, both for development and production purpose.

## Using in package.json

You should put these commands in the `package.json`:

```json
"scripts": {
  "dev": "nuxt",
  "build": "nuxt build",
  "start": "nuxt start",
  "generate": "nuxt generate"
}
```

Then, you can launch your commands via `yarn <command>` or `npm run <command>` (example: `yarn dev` / `npm run dev`).

## Development Environment

To launch Nuxt in development mode with hot module replacement:

<code-group>

  <code-block label="Yarn" active>

```bash
yarn dev
```

  </code-block>

  <code-block label="NPM">

```bash
npm run dev
```

  </code-block>
</code-group>

## List of Commands

You can run different commands depending on the [target](/guides/features/deployment-targets):

### target: `server` (default value)

- **nuxt dev** - Launch a development server on `http://localhost:3000` with hot-reloading.
- **nuxt build** - Build and optimize your application with webpack for production.
- **nuxt start** - Start the production server (after running `nuxt build`). Use it for Node.js hosting like Heroku, Digital Ocean, etc.

### target: `static`

- **nuxt dev** - Launch a development server on `http://localhost:3000` with hot-reloading.
- **nuxt generate** - Build the application (if needed), generate every route as a HTML file and statically export to `/dist` (used for static hosting).
- **nuxt start** - serve the dist/ directory like your static hosting would do (Netlify, Vercel, Surge, etc), great for testing before deploying.

## Production Deployment

Nuxt.js lets you choose between Server or Static deployments.

### Server Deployment

To deploy a SSR application we use `target: server`, where server is the default value.

<code-group>
  <code-block label="Yarn" active>

```bash
yarn build
```

  </code-block>
  <code-block label="NPM">

```bash
npm run build
```

  </code-block>
</code-group>

Nuxt.js will create a `.nuxt` folder with everything inside ready to be deployed on your server hosting.

<base-alert type="info">

we recommend putting `.nuxt` in `.npmignore` or `.gitignore`.

</base-alert>

Once your application is built you can use the `start` command to see a production version of your application.

<code-group>
  <code-block label="Yarn" active>

```bash
yarn start
```

  </code-block>
  <code-block label="NPM">

```bash
npm run start
```

  </code-block>
</code-group>

<base-alert type="info">

use PORT=4000 nuxt start when using pwa module

</base-alert>

### Static Deployment (Pre-rendered)

Nuxt.js gives you the ability to host your web application on any static hosting.

To deploy a static generated site make sure you have `target: static` in your `nuxt.config.js`.(For Nuxt >= 2.13:)

```js{}[nuxt.config.js]
export default {
  target: 'static'
}
```

<code-group>
  <code-block label="Yarn" active>

```bash
yarn generate
```

  </code-block>
  <code-block label="NPM">

```bash
npm run generate
```

  </code-block>
</code-group>

Nuxt.js will create a `dist` folder with everything inside ready to be deployed on a static hosting service.

As of Nuxt v2.13 there is a crawler installed that will now crawl your link tags and generate your routes when using the command `nuxt generate` based on those links.

<base-alert>

**Warning:** dynamic routes are ignored by the `generate` command when using Nuxt <= v2.12: [API Configuration generate](/guides/configuration-glossary/configuration-generate)

</base-alert>

<base-alert type="info">

When generating your web application with `nuxt generate`, [the context](/guides/internals-glossary/context) given to [asyncData](/guides/features/data-fetching#async-data) and [fetch](/guides/features/data-fetching#the-fetch-hook) will not have `req` and `res`.

</base-alert>

#### **Fail on Error**

To return a non-zero status code when a page error is encountered and let the CI/CD fail the deployment or build, you can use the `--fail-on-error` argument.

<code-group>
  <code-block label="Yarn" active>

```bash
yarn generate --fail-on-error
```

  </code-block>
  <code-block label="NPM">

```bash
npm run generate --fail-on-error
```

  </code-block>

</code-group>

## What's next?

<base-alert type="next">

Read our [FAQ](/faq) to find examples for deployments to popular hosts.

</base-alert>

</div>