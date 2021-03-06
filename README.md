# Markdown-it Named Headers

A plugin for [markdown-it](https://github.com/markdown-it/markdown-it). Makes header elments have name attributes.

```
# Example Header   -->   <h1 name="example-header">Example</h1>
```

By default, it uses [string.js](http://stringjs.com/)'s [slugify](http://stringjs.com/#methods/slugify) to translate header text into a url safe name. You can override this. See _Options_.

Cribbed heavily from https://github.com/valeriangalliat/markdown-it-anchor

## Install

```
npm install --save-dev markdown-it-named-headers
```

## Usage

Use with plain old node:

```js
var md   = require('markdown-it'),
    mdnh = require('markdown-it-named-headers');

md.use(mdnh, options);
```

Use as part of a Gulp workflow: (Note: You don't need to require named-headers in your gulpfile. gulp-markdown-it takes care of that for you).

```js
var gulp = require('gulp'),
    md = require('gulp-markdown-it');
gulp.task('md', [], function() {
    return gulp.src( '**/*.md' )
        .pipe(md({
            plugins: ['markdown-it-named-headers']
        }))
        .pipe(gulp.dest('dist'));
});
```


### Options

```js
{
   slugify: my_slug_function // default string.js's slugify()
}
```

If string.js's slugify doesn't fit your needs, you can simply pass in your own slugify function. The API is simple: accept any string, return a string suitable for a name attribute. Example:

```js
function slugify(input_string) {
    var output_string = my_transform_logic(input_string);
    return output_string;
}
```
