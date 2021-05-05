# starskyfood
####*small Website for educational purposes*

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
