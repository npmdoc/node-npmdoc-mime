# api documentation for  [mime (v1.3.4)](https://github.com/broofa/node-mime)  [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-mime.svg)](https://travis-ci.org/npmdoc/node-npmdoc-mime)
#### A comprehensive library for mime-type mapping

[![NPM](https://nodei.co/npm/mime.png?downloads=true)](https://www.npmjs.com/package/mime)

[![apidoc](https://npmdoc.github.io/node-npmdoc-mime/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-mime_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-mime/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-mime/build/screen-capture.npmPackageListing.svg)



# package.json

```json

{
    "author": {
        "name": "Robert Kieffer",
        "email": "robert@broofa.com",
        "url": "http://github.com/broofa"
    },
    "bin": {
        "mime": "cli.js"
    },
    "bugs": {
        "url": "https://github.com/broofa/node-mime/issues"
    },
    "contributors": [
        {
            "name": "Benjamin Thomas",
            "email": "benjamin@benjaminthomas.org",
            "url": "http://github.com/bentomas"
        }
    ],
    "dependencies": {},
    "description": "A comprehensive library for mime-type mapping",
    "devDependencies": {
        "mime-db": "^1.2.0"
    },
    "directories": {},
    "dist": {
        "shasum": "115f9e3b6b3daf2959983cb38f149a2d40eb5d53",
        "tarball": "https://registry.npmjs.org/mime/-/mime-1.3.4.tgz"
    },
    "gitHead": "1628f6e0187095009dcef4805c3a49706f137974",
    "homepage": "https://github.com/broofa/node-mime",
    "keywords": [
        "util",
        "mime"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "https://raw.github.com/broofa/node-mime/master/LICENSE"
        }
    ],
    "main": "mime.js",
    "maintainers": [
        {
            "name": "broofa",
            "email": "robert@broofa.com"
        },
        {
            "name": "bentomas",
            "email": "benjamin@benjaminthomas.org"
        }
    ],
    "name": "mime",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "url": "git+https://github.com/broofa/node-mime.git",
        "type": "git"
    },
    "scripts": {
        "prepublish": "node build/build.js > types.json",
        "test": "node build/test.js"
    },
    "version": "1.3.4"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module mime](#apidoc.module.mime)
1.  [function <span class="apidocSignatureSpan">mime.</span>Mime ()](#apidoc.element.mime.Mime)
1.  object <span class="apidocSignatureSpan">mime.</span>Mime.prototype
1.  object <span class="apidocSignatureSpan">mime.</span>charsets
1.  object <span class="apidocSignatureSpan">mime.</span>extensions
1.  object <span class="apidocSignatureSpan">mime.</span>types
1.  string <span class="apidocSignatureSpan">mime.</span>default_type

#### [module mime.Mime](#apidoc.module.mime.Mime)
1.  [function <span class="apidocSignatureSpan">mime.</span>Mime ()](#apidoc.element.mime.Mime.Mime)

#### [module mime.Mime.prototype](#apidoc.module.mime.Mime.prototype)
1.  [function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>define (map)](#apidoc.element.mime.Mime.prototype.define)
1.  [function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>extension (mimeType)](#apidoc.element.mime.Mime.prototype.extension)
1.  [function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>load (file)](#apidoc.element.mime.Mime.prototype.load)
1.  [function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>lookup (path, fallback)](#apidoc.element.mime.Mime.prototype.lookup)

#### [module mime.charsets](#apidoc.module.mime.charsets)
1.  [function <span class="apidocSignatureSpan">mime.charsets.</span>lookup (mimeType, fallback)](#apidoc.element.mime.charsets.lookup)



# <a name="apidoc.module.mime"></a>[module mime](#apidoc.module.mime)

#### <a name="apidoc.element.mime.Mime"></a>[function <span class="apidocSignatureSpan">mime.</span>Mime ()](#apidoc.element.mime.Mime)
- description and source-code
```javascript
function Mime() {
  // Map of extension -> mime type
  this.types = Object.create(null);

  // Map of mime type -> extension
  this.extensions = Object.create(null);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.mime.Mime"></a>[module mime.Mime](#apidoc.module.mime.Mime)

#### <a name="apidoc.element.mime.Mime.Mime"></a>[function <span class="apidocSignatureSpan">mime.</span>Mime ()](#apidoc.element.mime.Mime.Mime)
- description and source-code
```javascript
function Mime() {
  // Map of extension -> mime type
  this.types = Object.create(null);

  // Map of mime type -> extension
  this.extensions = Object.create(null);
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.mime.Mime.prototype"></a>[module mime.Mime.prototype](#apidoc.module.mime.Mime.prototype)

#### <a name="apidoc.element.mime.Mime.prototype.define"></a>[function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>define (map)](#apidoc.element.mime.Mime.prototype.define)
- description and source-code
```javascript
define = function (map) {
  for (var type in map) {
    var exts = map[type];
    for (var i = 0; i < exts.length; i++) {
      if (process.env.DEBUG_MIME && this.types[exts]) {
        console.warn(this._loading.replace(/.*\//, ''), 'changes "' + exts[i] + '" extension type from ' +
          this.types[exts] + ' to ' + type);
      }

      this.types[exts[i]] = type;
    }

    // Default extension is the first one we encounter
    if (!this.extensions[type]) {
      this.extensions[type] = exts[0];
    }
  }
}
```
- example usage
```shell
...

(The logic for charset lookups is pretty rudimentary.  Feel free to suggest improvements.)

## API - Defining Custom Types

Custom type mappings can be added on a per-project basis via the following APIs.

### mime.define()

Add custom mime/extension mappings

'''js
mime.define({
'text/x-some-format': ['x-sf', 'x-sft', 'x-sfml'],
'application/x-my-type': ['x-mt', 'x-mtt'],
...
```

#### <a name="apidoc.element.mime.Mime.prototype.extension"></a>[function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>extension (mimeType)](#apidoc.element.mime.Mime.prototype.extension)
- description and source-code
```javascript
extension = function (mimeType) {
  var type = mimeType.match(/^\s*([^;\s]*)(?:;|\s|$)/)[1].toLowerCase();
  return this.extensions[type];
}
```
- example usage
```shell
...
mime.lookup('.TXT');                      // => 'text/plain'
mime.lookup('htm');                       // => 'text/html'
'''

### mime.default_type
Sets the mime type returned when 'mime.lookup' fails to find the extension searched for. (Default is 'application/octet-stream'.)

### mime.extension(type)
Get the default extension for 'type'

'''js
mime.extension('text/html');                 // => 'html'
mime.extension('application/octet-stream');  // => 'bin'
'''
...
```

#### <a name="apidoc.element.mime.Mime.prototype.load"></a>[function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>load (file)](#apidoc.element.mime.Mime.prototype.load)
- description and source-code
```javascript
load = function (file) {
  this._loading = file;
  // Read file and split into lines
  var map = {},
      content = fs.readFileSync(file, 'ascii'),
      lines = content.split(/[\r\n]+/);

  lines.forEach(function(line) {
    // Clean up whitespace/comments, and split into fields
    var fields = line.replace(/\s*#.*|^\s*|\s*$/g, '').split(/\s+/);
    map[fields.shift()] = fields;
  });

  this.define(map);

  this._loading = null;
}
```
- example usage
```shell
...

The first entry in the extensions array is returned by 'mime.extension()'. E.g.

'''js
mime.extension('text/x-some-format'); // => 'x-sf'
'''

### mime.load(filepath)

Load mappings from an Apache ".types" format file

'''js
mime.load('./my_project.types');
'''
The .types file format is simple -  See the 'types' dir for examples.
...
```

#### <a name="apidoc.element.mime.Mime.prototype.lookup"></a>[function <span class="apidocSignatureSpan">mime.Mime.prototype.</span>lookup (path, fallback)](#apidoc.element.mime.Mime.prototype.lookup)
- description and source-code
```javascript
lookup = function (path, fallback) {
  var ext = path.replace(/.*[\.\/\\]/, '').toLowerCase();

  return this.types[ext] || fallback || this.default_type;
}
```
- example usage
```shell
...
E.g.

    > mime scripts/jquery.js
    application/javascript

## API - Queries

### mime.lookup(path)
Get the mime type associated with a file, if no mime type is found 'application/octet-stream' is returned. Performs a case-insensitive
 lookup using the extension in 'path' (the substring after the last '/' or '.').  E.g.

'''js
var mime = require('mime');

mime.lookup('/path/to/file.txt');         // => 'text/plain'
mime.lookup('file.txt');                  // => 'text/plain'
...
```



# <a name="apidoc.module.mime.charsets"></a>[module mime.charsets](#apidoc.module.mime.charsets)

#### <a name="apidoc.element.mime.charsets.lookup"></a>[function <span class="apidocSignatureSpan">mime.charsets.</span>lookup (mimeType, fallback)](#apidoc.element.mime.charsets.lookup)
- description and source-code
```javascript
lookup = function (mimeType, fallback) {
  // Assume text types are utf8
  return (/^text\//).test(mimeType) ? 'UTF-8' : fallback;
}
```
- example usage
```shell
...
E.g.

    > mime scripts/jquery.js
    application/javascript

## API - Queries

### mime.lookup(path)
Get the mime type associated with a file, if no mime type is found 'application/octet-stream' is returned. Performs a case-insensitive
 lookup using the extension in 'path' (the substring after the last '/' or '.').  E.g.

'''js
var mime = require('mime');

mime.lookup('/path/to/file.txt');         // => 'text/plain'
mime.lookup('file.txt');                  // => 'text/plain'
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
