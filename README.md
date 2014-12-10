
# fs-temp

`fs-temp` is a quick and simple way to create temporary files and directories.

Why another one? I know that there are already libraries doing similar things,
but I felt that their implementation was unnecessary complicated. I also wanted
a quick way to turn a buffer into a file.

## Installation

```sh
npm install --save fs-temp
```

## Usage

```js
var temp = requrie('fs-temp');

var data = new Buffer('testing 1 2 3');
vad path = temp.writeFileSync(data);

// `path` now holds the path to a file with the specified `data`
```

```js
var temp = require('fs-temp');

var path = temp.template('linusu-%s').mkdirSync();

// `path` now holds the path to a directory with the prefix "linusu-"
```

## API

The api mimics the one provided by `fs` very closely.

### `.open(flags[, mode], callback)`

Asynchronous file open.

`flags` is either `'w'` (only writing) or `'w+'` (writing and reading).

The callback gets two arguments `(err, obj)`. `obj` has `fd` and `path`.

### `.openSync(flags[, mode])`

Synchronous version of `.open()`, returns `obj` with `fd` and `path`.

### `.mkdir([mode, ]callback)`

Creates an empty directory.

The callback gets two arguments `(err, path)`.

### `.mkdirSync([mode])`

Synchronous version of `.mkdir()`, returns `path`.

### `.writeFile(data[, encoding], callback)`

Asynchronously writes data to a file. `data` can be a string or a buffer. The
`encoding` argument is ignored if `data` is a buffer. It defaults to `'utf8'`.

The callback gets two arguments `(err, path)`.

### `.writeFileSync(data[, encoding])`

Synchronous version of `.writeFileSync()`, returns `path`.

### `.template(template)`

Returns a copy of the module that uses the specified `template` when generating
file names. `template` should be a string where `%s` will be replaced with some
random characters (e.g. `"linusu-%s"`).

## License

The MIT License (MIT)

Copyright (c) 2014 Linus Unnebäck