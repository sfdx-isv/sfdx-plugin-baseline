sfdx-plugin-baseline
====================

Example of the auto-generated output of the sfdx plugins:generate command. Allows tracking to changes of the baseline plugin scaffolding over time.

[![Version](https://img.shields.io/npm/v/sfdx-plugin-baseline.svg)](https://npmjs.org/package/sfdx-plugin-baseline)
[![CircleCI](https://circleci.com/gh/VivekMChawla/sfdx-plugin-baseline/tree/master.svg?style=shield)](https://circleci.com/gh/VivekMChawla/sfdx-plugin-baseline/tree/master)
[![Appveyor CI](https://ci.appveyor.com/api/projects/status/github/VivekMChawla/sfdx-plugin-baseline?branch=master&svg=true)](https://ci.appveyor.com/project/heroku/sfdx-plugin-baseline/branch/master)
[![Codecov](https://codecov.io/gh/VivekMChawla/sfdx-plugin-baseline/branch/master/graph/badge.svg)](https://codecov.io/gh/VivekMChawla/sfdx-plugin-baseline)
[![Greenkeeper](https://badges.greenkeeper.io/VivekMChawla/sfdx-plugin-baseline.svg)](https://greenkeeper.io/)
[![Known Vulnerabilities](https://snyk.io/test/github/VivekMChawla/sfdx-plugin-baseline/badge.svg)](https://snyk.io/test/github/VivekMChawla/sfdx-plugin-baseline)
[![Downloads/week](https://img.shields.io/npm/dw/sfdx-plugin-baseline.svg)](https://npmjs.org/package/sfdx-plugin-baseline)
[![License](https://img.shields.io/npm/l/sfdx-plugin-baseline.svg)](https://github.com/VivekMChawla/sfdx-plugin-baseline/blob/master/package.json)

<!-- toc -->
* [Debugging your plugin](#debugging-your-plugin)
<!-- tocstop -->
<!-- install -->
<!-- usage -->
```sh-session
$ npm install -g sfdx-plugin-baseline
$ sfdx-plugin-baseline COMMAND
running command...
$ sfdx-plugin-baseline (-v|--version|version)
sfdx-plugin-baseline/0.0.0 darwin-x64 node-v10.12.0
$ sfdx-plugin-baseline --help [COMMAND]
USAGE
  $ sfdx-plugin-baseline COMMAND
...
```
<!-- usagestop -->
<!-- commands -->
* [`sfdx-plugin-baseline hello:org [FILE]`](#sfdx-plugin-baseline-helloorg-file)

## `sfdx-plugin-baseline hello:org [FILE]`

print a greeting and your org IDs

```
USAGE
  $ sfdx-plugin-baseline hello:org [FILE]

OPTIONS
  -f, --force                                      example boolean flag
  -n, --name=name                                  name to print
  -u, --targetusername=targetusername              username or alias for the target org; overrides default target org
  -v, --targetdevhubusername=targetdevhubusername  username or alias for the dev hub org; overrides default dev hub org
  --apiversion=apiversion                          override the api version used for api requests made by this command
  --json                                           format output as json
  --loglevel=(trace|debug|info|warn|error|fatal)   logging level for this command invocation

EXAMPLES
  $ sfdx hello:org --targetusername myOrg@example.com --targetdevhubusername devhub@org.com
     Hello world! This is org: MyOrg and I will be around until Tue Mar 20 2018!
     My hub org id is: 00Dxx000000001234
  
  $ sfdx hello:org --name myname --targetusername myOrg@example.com
     Hello myname! This is org: MyOrg and I will be around until Tue Mar 20 2018!
```

_See code: [src/commands/hello/org.ts](https://github.com/VivekMChawla/sfdx-plugin-baseline/blob/v0.0.0/src/commands/hello/org.ts)_
<!-- commandsstop -->
<!-- debugging-your-plugin -->
# Debugging your plugin
We recommend using the Visual Studio Code (VS Code) IDE for your plugin development. Included in the `.vscode` directory of this plugin is a `launch.json` config file, which allows you to attach a debugger to the node process when running your commands.

To debug the `hello:org` command: 
1. Start the inspector
  
If you linked your plugin to the sfdx cli, call your command with the `dev-suspend` switch: 
```sh-session
$ sfdx hello:org -u myOrg@example.com --dev-suspend
```
  
Alternatively, to call your command using the `bin/run` script, set the `NODE_OPTIONS` environment variable to `--inspect-brk` when starting the debugger:
```sh-session
$ NODE_OPTIONS=--inspect-brk bin/run hello:org -u myOrg@example.com
```

2. Set some breakpoints in your command code
3. Click on the Debug icon in the Activity Bar on the side of VS Code to open up the Debug view.
4. In the upper left hand corner of VS Code, verify that the "Attach to Remote" launch configuration has been chosen.
5. Hit the green play button to the left of the "Attach to Remote" launch configuration window. The debugger should now be suspended on the first line of the program. 
6. Hit the green play button at the top middle of VS Code (this play button will be to the right of the play button that you clicked in step #5).
<br><img src=".images/vscodeScreenshot.png" width="480" height="278"><br>
Congrats, you are debugging!
