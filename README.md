# gulp-js-string

A [gulp](https://github.com/gulpjs/gulp) plugin for exporting contents as string.

## Installation

```
$ npm install --save-dev gulp-js-string
```

## Usage

```javascript
var jsString = require('gulp-js-string');

gulp.src('./views/*.bhtml')
    .pipe(jsString())
    .pipe(gulp.dest('./dist'));
```

Input: `index.html`:

```html
<p>meow...meow...</p>
```

Output: `index.js`:

```javascript
module.exports = '<p>meow...meow...</p>';
```

## Configuration

Optionally, the variable name can be configured:

```javascript
var jsString = require('gulp-js-string');

gulp.src('./views/*.bhtml')
    .pipe(jsString(function(file) {
        return "exports." + file.basename.split('.')[0];
    }))
    .pipe(gulp.dest('./dist'));
```

Input: `index.html`:

```html
<p>meow...meow...</p>
```

Output: `index.js`:

```javascript
exports.index = '<p>meow...meow...</p>';
```

This is espacially useful if used in combination with `gulp-concat` to merge several files.

## License

[MIT](LICENSE)

## Author

[bouzuya][user] &lt;[m@bouzuya.net][email]&gt; ([http://bouzuya.net][url])

[user]: https://github.com/bouzuya
[email]: mailto:m@bouzuya.net
[url]: http://bouzuya.net
