# JSON Schema Markdown Tools

Documenting and validating complex JSON Schemas can be hard. This tool makes it easier by providing a number of scripts that can turn JSON Schema files into readable Markdown documentation that is ready for consumption on GitHub or processed using Jekyll or other static site generators.

These tools have been introduced by Adobe to document Adobe's Experience Data Models (XDM), but can be used for other JSON Schema documents, too.

## Requirements

- `npm` version 3.10.8 or up
- `node` v6 or up

## Installing and running

```bash
# clone XDM project
$ git clone git@git.corp.adobe.com:AdobeCloudPlatform/xdm.git

# clone this project
$ git clone git@git.corp.adobe.com:AdobeCloudPlatform/jsonschema2md.git

# install dependencies
$ cd jsonschema2md && npm install

# show usage information
$ node cli.js

# run task
$ node cli.js -d ../xdm/schemas/external/
# generated output for whole folder is written to ./out
```

### Installing the `jsonschema2md` Command Line Tools

The JSON Schema Markdown tools also includes a convenient `jsonschema2md` command line tool that can be installed using:

```bash
$ npm link
```

The command line arguments are identical between the `jsonschema2md` binary and the `cli.js` node script.

## Using JSON Schema Markdown Tools from `npm`

You can conveniently use the JSON Schema Markdown Tools from `npm`. This makes it possible to set up a conversion toolchain for your JSON Schema project that is driven entirely by `npm`. To do so, first define the dependency by adding this to your `"devDependencies"` section of `package.json`

```json
  "devDependencies": {
    "jsonschema2md": "git+ssh://git@git.corp.adobe.com:AdobeCloudPlatform/jsonschema2md.git"
  }
```

Then add the following to the `"scripts"` section of your `package.json` and adapt accordingly:

```json
"scripts": {
  "prepare": "mkdir -p docs/reference && jsonschema2md -o docs/reference -d schemas/draft-04
}
```

If you run `npm install` before running `npm run prepare`, `npm` will install the `jsonschema2md` in a `node_modules/.bin` path, even if you did not install the JSON Schema Markdown beforehand.

## Tests

Ensure you have all the dependencies installed via `npm install`, then run:

```bash
npm test
```

## TODOs

* JSON Schema validation:
  * property naming convention
  * vocabulary spellchecking

## Style Guide / Linting

This project uses [eslint](https://eslint.org) to enforce JavaScript coding style. To run the linter:

```bash
npm run lint
```

## Contributing

Please see [Contributing.md](Contributing.md) for details. Pull requests are welcome.

## License/Copyright

Copyright 2017 Adobe Systems Incorporated. All rights reserved.
This file is licensed to you under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License. You may obtain a copy
of the License at http://www.apache.org/licenses/LICENSE-2.0
