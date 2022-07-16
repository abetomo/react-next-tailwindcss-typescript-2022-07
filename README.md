# react-next-tailwindcss-typescript-2022-07

## create-next-app

```
% npx create-next-app --typescript example
Need to install the following packages:
  create-next-app
Ok to proceed? (y)
...
```

```
% cd example/
```

## `@types/node`

Installed `@types/node` with the following error message.

```
% npm run dev

> example@0.1.0 dev
> next dev

ready - started server on 0.0.0.0:3000, url: http://localhost:3000
It looks like you're trying to use TypeScript but do not have the required package(s) installed.

Please install @types/node by running:

	npm install --save-dev @types/node

If you are not trying to use TypeScript, please remove the tsconfig.json file from your package root (and any TypeScript files in your pages directory).
```

## Tailwind CSS

(In `example` directory.)

```
% npm install -D tailwindcss@latest postcss@latest autoprefixer@latest
```

```
% npx tailwindcss init -p

Created Tailwind CSS config file: tailwind.config.js
Created PostCSS config file: postcss.config.js
```

### `tailwind.config.js`

```diff
 /** @type {import('tailwindcss').Config} */
 module.exports = {
-  content: [],
+  content: [
+    './pages/**/*.{js,ts,jsx,tsx}',
+  ],
   theme: {
     extend: {},
   },
```

### `pages/_app.tsx`

```diff
-import '../styles/globals.css'
+import 'tailwindcss/tailwind.css'
 import type { AppProps } from 'next/app'

 function MyApp({ Component, pageProps }: AppProps) {
```

```
% rm styles/globals.css
```

## Lint

```
% npx next lint
```

### `package.json`

```diff
   "version": "0.1.0",
   "private": true,
   "scripts": {
+    "lint": "next lint",
     "dev": "next dev",
     "build": "next build",
     "start": "next start"
```

### `eslint-plugin-tailwindcss`

```
% npm install -D eslint-plugin-tailwindcss
```

### `.eslintrc.json`

```diff
 {
-  "extends": "next/core-web-vitals"
+  "extends": [
+    "next/core-web-vitals",
+    "plugin:tailwindcss/recommended"
+  ]
 }
```

### SSG

https://github.com/abetomo/react-next-tailwindcss-typescript-2021-11#ssg

## links

* https://nextjs.org/docs
* https://tailwindcss.com/docs/guides/nextjs
