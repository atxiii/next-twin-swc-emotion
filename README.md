# SWC compiler & Babel Plugin Macros
Make your next12 with SWC compiler & twin.macro + emotion.

Also there is another repository from c-rick that you can use it for [tailwind + styled-component](https://github.com/c-rick/next-twin). 

## How to use

First of all, you need replace the directories with your directories that included the emotion & tailwind.
so open `next-twin.js` and modify it.

```js
// next-twin.js
// ...
// replace your directories
    const componentsDir = path.resolve(__dirname, "_includes");
    const pagesDir = path.resolve(__dirname, "pages");
    const layoutDir = path.resolve(__dirname, "_layout");
// ...  
```        

Then you need to edit the next.config.js file.

- Nextjs config with one plugin: 

```js
// next.config.js
const withTwin = require('./next-twin.js');

const nextConfig = {
  reactStrictMode: true,
  // ...
};

module.exports = withTwin(nextConfig);

```

- Nextjs config with multiple plugins: 

```js
const withPlugins = require('next-compose-plugins');
const { withContentlayer } = require('next-contentlayer');
const withTwin = require('./next-twin.js');

const nextConfig = {
  reactStrictMode: true,
  // ...
};

const contentLayer = withContentlayer()({
  nextConfig,
});

const twin = withTwin(nextConfig);

module.exports = withPlugins([contentLayer, twin], nextConfig);
```





