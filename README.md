Gulp Subtree
============

A little gulp module to let you push a folder to a git subtree without keeping that folder in your git history. Highly recommend to use with [gulp-clean](https://www.npmjs.org/package/gulp-clean).

# IMPORTANT!

In order for Gulp Subtree to work correctly, the folder you are pushing **MUST NOT BE IGNORED THROUGH GIT**. Often, this is the `dist` folder. This is because Gulp Subtree needs to be able to temporarly add it to your Git repository in order to push it. For this reason, it's recommended to pair with [gulp-clean](https://www.npmjs.org/package/gulp-clean), allowing your distribution folder to be totally removed after it's been pushed.

## Usage

```js
var subtree = require('gulp-subtree');
var clean = require('gulp-clean');

gulp.task('subtree', function () {
	return gulp.src('dist')
		.pipe(subtree())
		.pipe(clean());
});
```

## Options

Options can be passed into subtree to choose the remote, branch, and message to push with. By default, it's `origin`, `gh-pages`, and `'Distribution Commit'`.

```js
var subtree = require('gulp-subtree');
var clean = require('gulp-clean');

gulp.task('subtree', function () {
	return gulp.src('dist')
		.pipe(subtree({
			remote: 'upstream',
			branch: 'master',
			message: 'Here We Go!'
		}));
});
```
