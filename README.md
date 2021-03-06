# [Webviz](https://webviz.io/) [![CircleCI](https://circleci.com/gh/cruise-automation/webviz.svg?style=svg)](https://circleci.com/gh/cruise-automation/webviz)

**Drag and drop your own bag files into [Webviz](https://webviz.io/app/?demo) to explore your robotics data, or connect to a live robot or simulation using the [rosbridge_server](http://wiki.ros.org/rosbridge_suite/Tutorials/RunningRosbridge).**

**Webviz** is a web-based application for playback and visualization of [ROS](http://www.ros.org/) [bag files](http://wiki.ros.org/Bags). This repository also contains some libraries that can be used independently to build web-based visualization tools.

- **webviz-core** ([homepage](https://webviz.io/), [tool](https://webviz.io/app), [github](https://github.com/cruise-automation/webviz/tree/master/packages/webviz-core)): A tool to inspect [ROS bags](http://wiki.ros.org/ROS/Tutorials/Recording%20and%20playing%20back%20data).
- **regl-worldview** ([homepage](https://webviz.io/worldview/), [npm](https://www.npmjs.com/package/regl-worldview), [github](https://github.com/cruise-automation/webviz/tree/master/packages/regl-worldview)): React library for rendering 2D and 3D scenes using [regl](https://github.com/regl-project/regl).
- **react-key-listener** ([npm](https://www.npmjs.com/package/react-key-listener), [github](https://github.com/cruise-automation/webviz/tree/master/packages/react-key-listener)): React component for handling keyboard events, without interfering with editable fields and buttons.
- **@cruise-automation/hooks** ([npm](https://www.npmjs.com/package/@cruise-automation/hooks), [github](https://github.com/cruise-automation/webviz/tree/master/packages/@cruise-automation/hooks)): A list of resusable React hooks.
- **@cruise-automation/button** ([npm](https://www.npmjs.com/package/@cruise-automation/button), [github](https://github.com/cruise-automation/webviz/tree/master/packages/@cruise-automation/button)): React button component that supports animated progress for destructive actions, "pulse" animation, and Bulma classes.
- **@cruise-automation/tooltip** ([npm](https://www.npmjs.com/package/@cruise-automation/tooltip), [github](https://github.com/cruise-automation/webviz/tree/master/packages/@cruise-automation/tooltip)): React component that uses [popper.js](https://popper.js.org/) to add rich, customizable tooltips to DOM elements.

Please see the individual package READMEs for details on how to install and use them.

## Slack

We have a [Slack workspace](https://github.com/cruise-automation/webviz/issues/461) to make it easier to ask questions and chat with other people who use Webviz. Join using the latest link posted [here](https://github.com/cruise-automation/webviz/issues/461).

## Running the static Webviz application

We recommend using the [hosted version of Webviz](https://webviz.io/app/?demo), which can connect to your [rosbridge_server](http://wiki.ros.org/rosbridge_suite/Tutorials/RunningRosbridge) or stream in bag data from your S3/GCS bucket. This way you'll always use the latest version of Webviz.

However, sometimes the hosted version is inconvenient, when streaming data from robots on the field where there is poor internet connectivity. For this it is useful to use a static build of webviz.

### Docker

The easiest way to use the static build, is to use our Docker image, which is automatically built on every commit to the `master` branch.

```sh
docker run -p 8080:8080 cruise/webviz
```

### Building manually

```sh
npm run bootstrap # install dependencies
npm run build # build all packages
npm run build-static-webviz # generate static build in __static_webviz__
npm run serve-static-webviz # serve static build on localhost:8080
```

## Developing

- `npm run bootstrap` in the root directory to install dependencies.
- `npm run build` to run a single build or `npm run watch` to watch and build.
- `npm run docs` to run the docs app (e.g. go to http://localhost:8080/app to open Webviz). Requires `build` to be run first.
- `npm run storybook` to run storybook. Requires `build` to be run first.
- `npm run screenshot-local` or `npm run screenshot-local-debug` to generate screenshots from stories.
- `npm run lint` to run the linters (and `npm run lint:fix` to automatically fix issues).
- `npm run flow` to run Flow.
- `npm run flow-typed-rebuild` to update the flow-typed definitions (any time when changing packages).
- `npm test` to run tests.
- `npm run build-static-webviz` to make a special build of just the Webviz application in the `__static_webviz__` directory.
- `npm run serve-static-webviz` to host the contents of the `__static_webviz__` directory on `localhost:8080`.

If you have the right permissions, you can publish:

- `npm run publish` to publish npm packages.
- `npm run docs-deploy` to deploy that statically hosted website (this is also done automatically in CI on the master branch).

If you run into any issues, file an issue on Github or ask us on Slack (see above).

## Contributing

PRs, bug reports, and feature requests are welcome! Please observe [CONTRIBUTING.md](CONTRIBUTING.md) and [CODE_OF_CONDUCT.md](CODE_OF_CONDUCT.md) when making a contribution.

Note that while it's possible to fork Webviz to make your own custom version, we'd encourage you to use webviz.io/app and propose generic solutions that everyone would benefit from. Cruise also still has its own fork of Webviz, but long term we'd like to move away from that. For examples of generic features, see the Node Playground panel, using generic RViz markers in the 3d panel, streaming in bags from any cloud service, loading layouts hosted on arbitrary URLs, and so on. We'd love your creative ideas for making Webviz widely useful!
