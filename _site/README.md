# Morf-Jekyll

A starting point for Jekyll projects & prototypes.

Includes:
Jekyll
Gulp
BrowserSync
Single Purpose Class Library in Sass

## Authors
- Alex Bloom
- Spencer Harrison

## Design Objectives

## Technology Objectives

## Reminders



## Getting Started
Once you've cloned the repository, you'll be running the command 'gulp' in your terminal, but first we must install gulp and browsersync into our project. So:
`npm install gulp`
`npm install browsersync`

You have to init a gulp.

Thanks to
https://nvbn.github.io/2015/06/19/jekyll-browsersync/

First of all, init a new package and install all dependencies:

`
npm init
sudo npm install -g gulp
npm install --save-dev gulp-shell lodash gulp browser-sync
`
That's installing (and saving as dependencies): gulp-shell, lodash, gulp, and browser-sync

(Did it tell you WARN? - update dependencies with npm update )

And create a gulpfile.js with:

`
var gulp = require('gulp');
var shell = require('gulp-shell');
var browserSync = require('browser-sync').create();

// Task for building blog when something changed:
gulp.task('build', shell.task(['bundle exec jekyll build --watch']));
// Or if you don't use bundle:
// gulp.task('build', shell.task(['jekyll build --watch']));

// Task for serving blog with Browsersync
gulp.task('serve', function () {
    browserSync.init({server: {baseDir: '_site/'}});
    // Reloads page when some of the already built files changed:
    gulp.watch('_site/**/*.*').on('change', browserSync.reload);
});

gulp.task('default', ['build', 'serve']);

`
Then add created files and folders to Jekyll exclude, otherwise gulp will found more than one task with the same name. In _config.yml:

`
exclude: [node_modules, gulpfile.js]
And that’s all! For running it:
`

gulp
