---
layout: post
title: "Learning Gulp"
date: 2018-06-17 14:01:01
image: 'http://drive.google.com/uc?export=view&id=1H2MlHjJ-TwTunyUIjVuQDo0BvniCwgl0'
description: The streaming build system.
category: 'web'
tags:
- web
- build
- gulp
twitter_text: The streaming build system.
introduction: The streaming build system.
---

## What is gulp?

- gulp is a tool that automates complex taske such as Sass(Css Extension language) compilation or web resource optimization.
- Based on Stream, you can take over th resuls of various plugins such as compression, merging, error handling, etc., and output the final result.

## Gulp Install & Start
```js
// 1. Gulp Install
# npm i gulp --global

// 2. Create a package.json file.
# npm init

// 3. Add gulp to devDependencies.
# npm i gulp --save -dev

// 4. Create gulpfile.js in the root path.
var gulp = require('gulp');
var gutil = require('gulp‐util');

gulp.task('default', function() {
    return gutil.log('Gulp is running!')
});

// 5. Run gulp
# gulp

[15:15:28] Using gulpfile c:\test\gulpfile.js
[15:15:28] Starting 'default'...
[15:15:28] Gulp is running!
[15:15:28] Finished 'default' after 11 ms
```

## Four essential APIs for gulp file configuration.
- gulp.task() - Assign and perform actions.
- gulp.src() - Path where the file will be returned after the operation.
- gulp.dest() - The path of the result after the final work.
- gulp.watch() - Specify what to do when changing the specified source.

## gulp.task()
- Commands for specifying and executing specific tasks.

```js
gulp.task('taskname', function(){
    // Add login to run.
;})
```

### task() API 형식

```js
gulp.task(name, [deps], fn)
```

- name : The name of the task. Whitespace is not allowed in the middle.
- deps : A list of tasks to be executed and completed before executing the task. Array type, options.
- fn : The function to which the task actually executes logic. options.

```js
gulp.task('task1', function(){
    var a = 1;
    var b = 2;

    console.log(a+b);
    console.log("task1 complete");
});

gulp.task('task2', ['task1'], function(){
    console.log("task2 execution.");
});

// Specify only those taske that should be preprocessed to perform build operations, except for funcion.
// The tasks are processed in parallel.
gulp.task('build', ['array', 'of', 'task', 'name']); 
```

### gulp task asynchronous processing
- Asynchronous processing is possible instead of sequential processing.

```js
// run a command in a shell 
var exec = require('child_process').exec; 
gulp.task('task1', function(cb) {
// build Jekyll 
    exec('task1 build', function(err) {
        if (err) return cb(err); // return error 
        cb(); // finished task 
    }); 
});
// use an async result in a pipe 
gulp.task('somename', function(cb) {
    getFilesAsync(function(err, res) {
        if (err) return cb(err);
        var stream = gulp.src(res).pipe(minify())
            .pipe(gulp.dest('build')) 
            .on('end', cb); // if the result of the aboce task1 operation is returned to the callback, the somename is executed.
    });
});
```

### The following is a method of stream processing.

```js
gulp.task('somename', function() {
    var stream = gulp.src('client/**/*.js')
        .pipe(minify())
        .pipe(gulp.dest('build')); 
    return stream; 
});
```

## gulp.src()
- The files in that location are returned as a stream of Vinyl files via the specified logic.
- You can use ```.pipe``` to pass the results to another plugin.
### src() API type

```js
gulp.src(globs, [optins])
```

- globs : One or more files can be specified as String or Array. See below.

```js
// When specifying a single file
gulp.src('client/*.js');

// When specifying multiple files
gulp.src(['client/*.js', '!client/b*.js', 'client/bad.js'])
// use '*' to specify multiple files.
//use '!' to exclude that file.
```

## gulp.dest()
- Specifies the file location where the final result value is to be output. If the folder does not exist in the path, create it.

```js
gulp.task('copyHtml', function(){
    gulp.src('source/*.html').pipe(gulp.dest('public'));
});
```

## gulp.watch()
- When a change is made to the first specified parameter(file), the operation of the second parameter(task) is performed.
```js
// if the js file under 'source/javascript' is changed, the 'jshint' task is executed.
gulp.watch('source/javascript/**/*.js', ['jshint']);
// returns an EventEmitter that fires a change event after execution.
```
### watch() API type
```js
gulp.watch(glob, [cb])
```
- glob : specifies the to monitor for changes to String or Array.
- cb(event) : the function to be called whenever there is a change in the specified file.
```js
gulp.watch('js/**/*.js', function(event){
    console.log('file ' + event.path + ' was ' + event.type + ', running tasks...');
    // event type : added, changed, deleted, renamed
    // event path : the path of the file that triggered the event 
})
```

## Gulp list of useful plugins
- Gulp Utility
- Gult Uglify
- Gulp Concat
- Sourcemap
- Gulp HTML min
- Gulp CSS nano
- Gulp Uncss
- Gulp Image-min

## Reference
- [Gulp js](https://gulpjs.com/)
- [Highly Useful Gulp Plugins](https://ilikekillnerds.com/2014/11/10-highly-useful-gulp-js-plugins-for-a-super-ninja-front-end-workflow/)
- [Scotch Gulp Tutorials](https://scotch.io/tutorials/automate-your-tasks-easily-with-gulp-js)
- [Gulp for Beginners](https://css-tricks.com/gulp-for-beginners/)