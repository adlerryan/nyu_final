# The JAMStack, AJAX and Static Site Generation

HTML final project for the template of an online ski store. 

- [11ty](https://www.11ty.dev/)
- [11ty Rocks](https://11ty.rocks)
- Andy Bell's [11ty](https://piccalil.li/course/learn-eleventy-from-scratch/) course.



### Initial Setup

Today we're are building a simple multipage [static website](https://zealous-kilby-113356.netlify.com) with an [ajax connection](https://zealous-kilby-113356.netlify.com/posts/ajax/) that fetches articles from the New York Times.

Create a `.gitignore` file at the top level targeting the node_modules folder:

```sh
node_modules
```

```sh
$ npm init -y
$ npm install @11ty/eleventy
```

Add a script to `package.json`:

```js
"scripts": {
  "start": "eleventy --serve"
},
```

Note: since 11ty renders Markdown files we need to either delete the readme.md file in this repo or create an `.eleventyignore` file with the contents `readme.md`. Here's the [documentation](https://www.11ty.dev/docs/ignores/) for Eleventy ignore files.

Note the `.prettierignore`:

```
# Ignore artifacts:
build
coverage

# Ignore all readme files:
readme.md
```

### Eleventy Configuration

Add [passthroughs](https://www.11ty.dev/docs/copy/) for our static assets in an `.eleventy.js` file.

```js
module.exports = function (config) {
  config.addPassthroughCopy("./src/css/");
  config.addPassthroughCopy("./src/img/");
  config.addPassthroughCopy("./src/js/");
};
```

This is our eleventy configuration file. It is a function that exports its contents for use by the Eleventy publishing system.

Add instructions for input and output folders:

```js
module.exports = function (config) {
  config.addPassthroughCopy("./src/css/");
  config.addPassthroughCopy("./src/img/");
  config.addPassthroughCopy("./src/js/");

  return {
    dir: {
      input: "src",
      output: "_site",
    },
  };
};
```

Run `npm start` and open the localhost address in Chrome.

Note:

- the generated `_site` folder
- the folders specified in our config are copied into `_site`


