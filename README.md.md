https://vitejs.dev/guide/

Vite requires Node.js version >=12.0.0.

For production: the default build targets browsers that support native ESM via script tags. Legacy browsers can be supported via the official @vitejs/plugin-legacy - see the Building for Production section for more details

***  MAYBE USE THIS FOR DEV PURPOSE ONLY! ***

To create a new project:

    `npm init @vitejs/app <project-name>`
    ´cd <project-name>´ 
    ´npm install´ 
    ´npm run dev´ 


Some Vue Vite features you should know
1 – Bundling your project for production
A goal for Vite was to make Vue development and production as easily as possible. And although there is no bundling during dev, it is super easy to bundle your project for production. 
All you have to do is run npm run build. 
If we look at package.json, we see that this is calling vite build – which like other build processes, will bundle your Vue project and prepare your dist folder to be served.  
2 – Managing asset URLS
    - Absolute, or
    - Relative
3 – Built-in Typescript support

