

To develop the project locally, you'll need a recent version of Node.js and `yarn` v1 installed globally.

To get started, clone the repo and run `yarn` from the root directory:

```bash
git clone repository
cd file name
yarn
```

Now that your dependencies are installed, you can run the local Next.js dev server:

```bash
yarn dev
```

You should now be able to open `http://localhost:3000` to view the webapp.

## Production

To build for production, you can run:

```bash
yarn build
```

Which just runs `next build` under the hood.

### Local-linked react-notion-x

Once you have `react-notion-x` set up locally, run `yarn link` from each `react-notion-x` package:

```bash
# from react-notion-x clone
cd packages/react-notion-x
yarn link
cd ../packages/notion-utils
yarn link
cd ../packages/notion-types
yarn link
cd ../packages/notion-client
yarn link
```


The last step is to make sure that the Next.js project and these local dependencies are all pointing to the same versions of `react` and `react-dom`.

```bash
# from react-notion-x clone
cd node_modules/react
yarn link
cd ../react-dom
yarn link
```

```bash
# from nextjs-notion-starter-kit
yarn link react react-dom
```

With this setup, in one tab, you can run `yarn dev` to keep `react-notion-x` up-to-date, and in another tab, you can run `yarn dev` to keep up-to-date.

### Gotchas

Whenever you make a change to one of the `react-notion-x` packages, it will automatically be recompiled into its respective `build` folder, and the `yarn dev` from  should hot-reload it in the browser.

Sometimes, this process gets a little out of whack, and if you're not sure what's going on, I usually just quit one or both of the `yarn dev` commands and restart them.

If you're seeing something unexpected while debugging with Next.js, try running `rm -rf .next` to refresh the Next.js cache before running `yarn dev` again.
