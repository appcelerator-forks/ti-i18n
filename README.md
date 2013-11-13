# Titanium i18n

Titanium i18n (*ti-i18n*) is both a [Titanium](http://docs.appcelerator.com/titanium/latest/#!/guide/Titanium_Command-Line_Interface_Reference) CLI 3.2+ hook and stand-alone CLI for managing your app's internationalization. For now, it does exactly what the soon to be deprecated `alloy extract-i18n` does. But this will soon be expanded with new options, for both [Alloy](http://docs.appcelerator.com/titanium/latest/#!/guide/Alloy_Command-Line_Interface_Reference) and Classic projects.

* Blogs on ti-i18n: [http://fokkezb.nl/tag/ti-i18n](http://fokkezb.nl/tag/ti-i18n)

[![NPM](https://nodei.co/npm/ti-i18n.png?downloads=true&starts=true)](https://nodei.co/npm/ti-i18n/)

## Quick Start

### Install from NPM
*ti-i18n* is built on [Node.js](http://nodejs.org/). Once you have Node.js installed you can use the included NPM package manager to install [ti-i18n](https://npmjs.org/package/ti-i18n) via the following command:

```
sudo npm install -g ti-i18n
```

### Install as Titanium CLI 3.2+ hook
If you already run the upcoming Titanium CLI 3.2, you can ask *ti-i18n* to install itself as an hook under the Titanium CLI:

```
ti-i18n hook
```

Once, you've done this. The following (note the `-`) does exactly the same:

```
ti-i18n extract

ti i18n extract
```

*ti-i18n* will be further developped to be a worthy hook, listen to the global flags like `--no-colors` and read any relevant defaults from the CLI config.

### Extract strings
By default *ti-i18n* scans the `i18n` directory and uses all of them. You can choose a specific language by passing it as the first argument after the `extract` command.

Add the `-a` or `--apply` option to append the new strings.

```
ti-i18n extract nl -a
```

#### What does it extract?
As demonstrated by the files in the [test/source](https://github.com/FokkeZB/ti-i18n/tree/master/test/source) directory, *ti-i18n* should be able to extract any string. Just don't use composed strings like:

```
L('error_' + code);
```

## Usage
Command | Availability | Option | Description
------- | ------------ | ------ | -----------
`extract`|both||extract i18n strings from the source code (js and tss files)
||`<language>`|Single lanuage to extract for
||`-a`, `--apply`|Update `strings.xml`
`hook`|stand-alone|hook ti-i18n into Titanium CLI as: `ti i18n`
`unhook`|both|unhook ti-i18n from Titanium CLI
`hooked`|stand-alone|check if ti-i18n is hooked into Titanium CLI

## Global options
Option | Availability | Description
------- | ----------- | -----------
`-h`, `--help`|both|output usage information
`-v`, `--version`|stand-alone|output the version number (as a hook, this will output the Titanium CLI version)

## Testing
The [test](https://github.com/FokkeZB/ti-i18n/tree/master/test) folder contains a single unit-test you can use, e.g. with mocha:

```
sudo npm install -g mocha
mocha test/test.js
```

## Roadmap

* ~~Rewrite `extract` to search through `XML`, `TSS` (JSON) and `JS` (AST).~~
* Option to remove second hint-argument from `L` and use it in `strings.xml`.
* Add `validate` to validate `strings.xml` for UTF-8, CDATA, duplicates etc.
* Add `clean` to comment out any strings not found in source.
* Add `peer` to make sure all language have same strings.
* Add `name` to create/update XML for internationalized app names.

## Thanks to

* [Chris Barber](https://twitter.com/cb1kenobi) for the awesome CLI hooks in 3.2
* Coffee

## License

<pre>
Copyright 2013 Fokke Zandbergen

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
</pre>
