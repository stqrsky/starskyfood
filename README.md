# starskyfood
####*small Website for educational purposes using TailwindCSS*

![foodstar.gif](public/img/foodstar.gif)

Quick Insight:
* Tailwind CSS
    * Setup
    * Install
    * base html template

See your results:
- `npm install live-server -g`
- `live-server public`

create tailwind-config-file for specific css-usage and to have the drop-down options in HTML:
- `npx tailwindcss init --full` (**--full** flag with all default values)

How to add fonts:
- src/styles.css -> @import url('....')

How to @apply directive of a number of classes to an individual customed class:
(avoid bloated code with lots of classes)
- src/styles.css -> 
```
.class{
  @apply bg-white rounded overflow-hidden shadow-md relative
  }
```


wiki: 
- tracking-wider (class) = space between letters
- hidden md:block (hide&seek)

##Steps using TailwindCSS with KirbyCMS:
1. create a new Kirby project:
```
composer create-project getkirby/plainkit my-project
```
2. switch to the project directory:
```
cd my-project
```
3. An empty *package.json* in the directory *my-project*. execute this:
```
npm init -y
```
4.  packages required and recommended for Tailwind CSS:
```
npm install tailwindcss postcss-cli autoprefixer postcss-nesting cross-env cssnano
```
5. All packages are  loaded into the node_modules folder  . The next step is to create the Tailwind CSS configuration file (tailwind.config.js). Do this with the command:
```
npx tailwind init
```
6. tailwind.config.js Then adjust the file  as follows:
```
module.exports = {
    purge: {
        preserveHtmlElements: false,
        content: [
            './site/templates/*.php',
            './site/snippets/*.php',
            './site/tailwind/*.css',
        ],
    },
    darkMode: false, // or 'media' or 'class'
    theme: {
        extend: {}
        },
    },
    variants: {
        extend: {},
    },
    plugins: [
    ],
}
```
7. we need the file postcss.config.js with the following content:
```
module.exports = {
  plugins: [
    require('tailwindcss'),
    require('postcss-nesting'),
    require('autoprefixer'),
    require('cssnano')({
      preset: 'default',
    }),
  ]
}
```
8. To site/tailwind/ do this, tailwind.css create the file
```
@tailwind base;
@tailwind components;
@tailwind utilities;
```
9. replace package.json the 'scripts' area in the file
```
"scripts": {
    "build": "postcss site/tailwind/tailwind.css -o assets/style.css",
    "watch": "postcss site/tailwind/tailwind.css -o assets/style.css --watch",
    "prod": "cross-env NODE_ENV=production postcss site/tailwind/tailwind.css -o assets/style.css"
},
```
10. three commands to generate the style.css
```
npm run build
npm run watch
npm run prod
```
11. in style.css in <head>
```
<?= css('assets/style.css') ?>
```
