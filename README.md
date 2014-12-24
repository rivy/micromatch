# micromatch [![NPM version](https://badge.fury.io/js/micromatch.svg)](http://badge.fury.io/js/micromatch)

> Glob matching for javascript/node.js. Like minimatch, but 10-40x faster.

 - 5-40x faster than minimatch ([benchmarks](#benchmarks))
 - Focus on core Bash 4.3 specification features that are actually used (or can be used) in node.js
 - Extensive unit tests

## Features

**Supports**

All the mainstream glob features you're used to using in your gulp and Grunt tasks:

 + [Brace Expansion] - ex. `foo/bar-{1..5}.md`, `one/{two,three}/four.md`
 + Globstar matching - ex. `**/*`, `a/b/*.js`

**Does not support**

 + [Extended glob matching][extended], like `(a|b)`. This might be supported in the future, either in core or as an extension, but it's hard to justify the cost in terms of speed and complexity for features that are rarely used.


## Install with [npm](npmjs.org)

```bash
npm i micromatch --save
```


## Usage

### micromatch()

```js
var micromatch = require('micromatch');

micromatch(['a.js', 'b.md', 'c.txt'], '*.{js,txt}');
//=> ['a.js', 'c.txt']
```

**Negation patterns:**

```js
micromatch(['a.js', 'b.md', 'c.txt'], '!*.{js,txt}');
//=> ['b.md']

micromatch(['a.md', 'b.js', 'c.txt', 'd.json'], ['*.*', '!*.{js,txt}']);
//=> ['a.md', 'd.json']
```

### micromatch.matchRe()

Generate a regular expression for matching file paths based on the given pattern:

```js
var
micromatch.makeRe('a/?/c.md');
//=> /^a\/.\/c\.md$/
```


## Benchmarks

Run the benchmarks

```bash
node benchmark/
```

![image](https://cloud.githubusercontent.com/assets/383994/5535193/1c28a4a2-8a45-11e4-813a-0236586aa990.png)


## Run tests

Install dev dependencies

```bash
npm i -d && mocha
```


## Contributing
Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/micromatch/issues)

Please be sure to run the benchmarks before/after any code changes to judge the impact before you do a PR. thanks!

## Author

**Jon Schlinkert**
 
+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert) 

## License
Copyright (c) 2014 Jon Schlinkert  
Released under the MIT license

***

_This file was generated by [verb](https://github.com/assemble/verb) on December 23, 2014._

[extended]: http://mywiki.wooledge.org/BashGuide/Patterns#Extended_Globs
[Brace Expansion]: https://github.com/jonschlinkert/braces