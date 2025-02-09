# templates/spa

This template leverages React Router SPA Mode and the React Router Vite Plugin to build your app as a Single-Page Application using Client Data for all of your data loads and mutations. It uses shadcnui for styling and components.

## SPA Mode Caveats

SPA Mode only works when using Vite and the Remix Vite plugin

You cannot use server APIs such as headers, loader, and action -- the build will throw an error if you export them

You can only export a HydrateFallback from your root.tsx in SPA Mode -- the build will throw an error if you export one from any other routes.

You cannot call serverLoader/serverAction from your clientLoader/clientAction methods since there is no running server -- those will throw a runtime error if called

## Setup

```shellscript
npx create-remix@latest --template remix-run/remix/templates/spa
```

## Development

You can develop your SPA app just like you would a normal Remix app, via:

```shellscript
npm run dev
```

## Production

When you are ready to build a production version of your app, `npm run build` will generate your assets and an `index.html` for the SPA.

```shellscript
npm run build
```

### Preview

You can preview the build locally with [vite preview](https://vitejs.dev/guide/cli#vite-preview) to serve all routes via the single `index.html` file:

```shellscript
npm run preview
```

> [!IMPORTANT]
>
> `vite preview` is not designed for use as a production server

### Deployment

You can then serve your app from any HTTP server of your choosing. The server should be configured to serve multiple paths from a single root `/index.html` file (commonly called "SPA fallback"). Other steps may be required if the server doesn't directly support this functionality.

For a simple example, you could use [sirv-cli](https://www.npmjs.com/package/sirv-cli):

```shellscript
npx sirv-cli build/client/ --single
```
