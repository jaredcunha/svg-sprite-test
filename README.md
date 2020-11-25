# USWDS Icon prototype

This is a prototype for how a team might modify a default svg icon sprite to suit the needs of their project. The default sprite will include only a handful of what the entire icon set provides in order to maintain a smaller footprint. 

This project uses the [USWDS Gulp file](https://github.com/uswds/uswds-gulp/), and the purpose is to test the workflow for managing the SVG sprite. 

The only thing that really matters is that the icons are working and that the workflow makes sense. 

## Getting started

First, you will need to clone this repo. Other dependencies include:
- [Node JS](http://nodejs.org)
- [Jekyll](http://jekyllrb.com)

```bash
$ npm install
$ bundle exec jekyll serve
```

Once Jekyll is running, visit [http://localhost:4000/](http://localhost:4000/).

## Updating the sprite. 

Take a look at the `/images` directory. You will notice two subdirectories titled `/usa-icons` and `/usa-icons/unused`. 

Everything inside of `usa-icons` is included by default in the icon sprite. Everything inside `usa-icons-unused` is part of the total icon set, but not included for use by default in the sprite.

To add an icon to the sprite, simply move any image from `usa-icons-unused` into `usa-icons`. 

Next, run the following command

```bash
$ gulp svg-sprite
``` 

Now go to `/layouts/default.html and scroll to line 121. 

The HTML use the svg sprite is:
```html
<svg class="usa-icon usa-icon--sm" aria-hidden="true">
   <use xlink:href="/images/sprite.svg#[ICON NAME WITHOUT .SVG]"></use>
</svg>
```

So if the icon you moved into `usa-icons` was named `bar_chart.svg`, the snippet to display the sprite would be:
```html
<svg class="usa-icon usa-icon--sm" aria-hidden="true">
   <use xlink:href="/images/sprite.svg#bar_chart"></use>
</svg>
```

Refresh the page to see if you can see your icon.
