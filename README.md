# ESPN Fantasy Football API
[![npm](https://img.shields.io/npm/v/espn-fantasy-football-api.svg?colorB=deepskyblue)](https://www.npmjs.com/package/espn-fantasy-football-api) [![Build Status](https://travis-ci.org/mkreiser/ESPN-Fantasy-Football-API.svg?branch=master)](https://travis-ci.org/mkreiser/ESPN-Fantasy-Football-API) [![Maintainability](https://api.codeclimate.com/v1/badges/548bae8930b5efad0418/maintainability)](https://codeclimate.com/github/mkreiser/ESPN-Fantasy-Football-API/maintainability) [![Test Coverage](https://api.codeclimate.com/v1/badges/548bae8930b5efad0418/test_coverage)](https://codeclimate.com/github/mkreiser/ESPN-Fantasy-Football-API/test_coverage) [![dependencies Status](https://david-dm.org/mkreiser/ESPN-Fantasy-Football-API/status.svg)](https://david-dm.org/mkreiser/ESPN-Fantasy-Football-API) [![devDependencies Status](https://david-dm.org/mkreiser/ESPN-Fantasy-Football-API/dev-status.svg)](https://david-dm.org/mkreiser/ESPN-Fantasy-Football-API?type=dev) [![Known Vulnerabilities](https://snyk.io/test/github/mkreiser/ESPN-Fantasy-Football-API/badge.svg?targetFile=package.json)](https://snyk.io/test/github/mkreiser/ESPN-Fantasy-Football-API?targetFile=package.json) [![Blazing Fast](https://img.shields.io/badge/speed-blazing%20%F0%9F%94%A5-brightgreen.svg)](https://twitter.com/acdlite/status/974390255393505280)

A Javascript API client for both web and NodeJS that connects to ESPN's fantasy football API. Available as an npm package.

## Features

* Supports leagues, matchups, boxscores, and rosters.
  * Get matchup details, player performances, league standings, historical data, and more.
  * Private league support.
* Highly documented.
* Built for speed and efficiency with caching support.
* Built for extensibility by using ES6 classes.

## Documentation Reference

Hosted documentation available at http://espn-fantasy-football-api.s3-website.us-east-2.amazonaws.com/.

## Installation

[![NPM](https://nodei.co/npm/espn-fantasy-football-api.png?compact=true)](https://nodei.co/npm/espn-fantasy-football-api/)

There are two files exported in the package:

* `dist/index-web.js` - Production file built for web environments (main/default file)

* `dist/index-node.js` - Production file built for node environments

## How to use

### Importing

```javascript
// Web
import { League, Team } from 'espn-fantasy-football-api';

// Node
import { League, Team } from 'espn-fantasy-football-api/dist/index-node.js';

// From local build
import { League, Team } from './dist/index-node.js';
```

### Loading a League

```javascript
import { League } from 'espn-fantasy-football-api';

const league = new League({ leagueId: 336358, seasonId: 2018 });
league.read().then(() => console.log(league)); // Prints loaded league
```

### Loading a Private League

```javascript
import { BaseAPIObject, League } from 'espn-fantasy-football-api';

BaseAPIObject.setCookies({ espnS2: 'xxxxx', SWID: '{xxxxxxxxxx}' }); // fire and forget

const league = new League({ leagueId: 336358, seasonId: 2018 });
league.read().then(() => console.log(league)); // Prints loaded league
```

## Roadmap

#### 0.7.0

- Improve passing of constructor params to nested classes - *#1 priority*
- Remove q dev dependency
- Address CodeClimate feedback
- Research an axios `get` only package
- Player caching - *May be bumped*
- Versioned documentation - *May be bumped*
- Clean up test suites - *May be bumped, not required for version bump*



#### 1.0.0

- Satisfied with stable pre-1.0.0 package

#### 1.1.0 

- Increased functional patterns, reduce data mutability
- Introduce Flow or TypeScript

## Testing

*How do you know it works?*

This project includes an expansive unit test suite as well as a live integration test suite. The integration tests make live calls to the ESPN API, ensuring that the project will work in the real world.

Travis CI is used to build and verify changes. Additionally, the master branch runs a weekly build on Travis.

## Built With

[axios](https://github.com/axios/axios) - Promise based HTTP client.

[babel](https://github.com/babel/babel) + [webpack](https://github.com/webpack/webpack) - Compiles and bundles ES6 and next-gen Javascript to browser-compatible Javascript.

[eslint](https://github.com/eslint/eslint) - Fast code linting to maintain good style and code patterns.

[jest](https://github.com/facebook/jest) - Powerful and fast testing platform.

[jsdoc](https://github.com/jsdoc3/jsdoc) - Generated code documentation.

[lodash](https://github.com/lodash/lodash) - Utility library.

## Versioning

This project uses [Semantic Versioning](https://semver.org/).

## License

This project is licensed under [LGPL-3.0](https://choosealicense.com/licenses/lgpl-3.0/) (see LICENSE for details). Essentially, don't take this project and close source it.

This is my first time writing OSS and picking a license. Feel free to reach out with questions and/or concerns.


## Contributing

See [CONTRIBUTING.MD](https://github.com/mkreiser/ESPN-Fantasy-Football-API/blob/master/CONTRIBUTING.md)

## npm scripts

| Script           | Description                                                  |
| ---------------- | ------------------------------------------------------------ |
| build            | Builds the module.                                           |
| build:docs       | Builds the docs.                                             |
| clean            | Runs all clean scripts.                                      |
| clean:dist       | Removes the dist folder.                                     |
| clean:docs       | Removes the docs folder.                                     |
| ci               | Runs continuous integration tasks. Currently runs lint, unit and integration tests, and build. |
| lint             | Ensures code style is correct.                               |
| serve:docs       | Builds and serves docs. Defaults to port 8080.               |
| test             | Starts a jest test runner with access to all tests. Pass `--watch` to keep jest alive and watching for changes. Pass a string as a file inclusion pattern. |
| test:all         | Runs the unit tests then the integration tests.              |
| test:integration | Runs the integration tests.                                  |
| test:unit        | Runs the unit tests.                                         |

## Acknowledgements

Thanks to the following projects for their work and documentation of the ESPN API. They served as the inspiration for this project.

[rbarton65/espnff](https://github.com/rbarton65/espnff)

[Possardt/espn-ff-api](https://github.com/Possardt/espn-ff-api)
