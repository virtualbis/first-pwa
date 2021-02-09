## Following this tutorial (https://www.codica.com/blog/how-to-create-pwa-with-react/)

- Create new folder for app in VS Code
- Create app with template for PWA `npx create-react-app first-pwa --template cra-template-pwa`
- If you want a Typescript compatible app use this template `npx create-react-app pwa-react-typescript --template typescript`
- Register a Service Worker in index.js. From `serviceWorkerRegistration.unregister();` to `serviceWorkerRegistration.register();`
- Make sure the manifest is in the index.html. It should have been generated with the template. It looks like this: `<link rel="manifest" href="/manifest.json">`.
- While you're in the index.html file rename your app here `<title>React App</title>`
- Configure the Web Application Manifest.Open the `manifest.json file` in public directory. At least change the name of the app from `"short_name": "React App", "name": "Create React App Sample",` to something like `"short_name": "First PWA", "name": "My First PWA",`

From Google about the manifest file:
_"The web app manifest is a simple JSON file that tells the browser about your web application and how it should behave when ‘installed’ on the user’s mobile device or desktop. Having a manifest is required by Chrome to show the Add to Home Screen prompt."_

That's it! But let's continue to show a little and deploy it

- In this tutorial they had us use react-router, the de facto routing solution for React. To add it to our project (and the required type definitions for TypeScript), we use: `npm add react-router-dom @types/react-router-dom`. Then look at how it's done in the app.js file.
- Code splitting: good way to improve loading times for PWAs is to ensure that the code is not built into big files.
  To do this replace in your app.js this: `import About from "./About"; import Home from "./Home";` with this: `const About = lazy(() => import('./About')); const Home = lazy(() => import('./Home'));`. See how it uses `<Suspense fallback={<div>Loading...</div>}>`.
  - Should look up more on "lazy" loading before using in production. Seemed to see a debate whether it is a good idea or not.

## Not sure how to do yet
