energiatietosovellus
====================

Energiatietosovelluksen koodit
Running

You need node.js and npm (comes with node). After cloning the repo, install all the dependencies:

npm install
And then run the application with:

node src/web
This will start the app in development mode - running against unconcatenated and unminified source files. To emulate how heroku runs the application, you need foreman:

foreman start
Which will start the app in production mode. Production mode runs the app against RequireJS optimized JavaScript sources.

Configuration

App configuration should be placed either in config.json, or passed in as environment variables:

google.maps.api.key: Google Maps API key
Building & testing

This project uses Grunt as the build tool of choice. You can install it with npm:

npm install -g grunt
Grunt can run all test suites (node, functional, client) with the following command:

grunt functional
Functional tests will kick off a node server, and point a PhantomJS instance to it. Client tests will test client-side code on the server with node.js.

Deployment

Deployment assumes that a heroku remote has been configured for the repository.

grunt deploy
This will first run JSLint against the codebase, then perform all tests (see above) and finally run the requirejs optimizer to concat and minify all sources into the /public/dist folder. Then these files will be committed to a separate branch, which is pushed to heroku master.
