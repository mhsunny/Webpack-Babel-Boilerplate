"# Webpack-Babel-Boilerplate" 


This is a boilerplate / template to start from scratch for any Mordern Javascript es6/7 which converts es6 JS file regular old Javascript. 
It will work for any old browsers and it will combine to a bundle.js file.


<pre>
<code>
    const path = require('path');

    module.exports = {
    entry: './src/index.js',
    output: {
        path: path.resolve(__dirname, 'dist/assets'),
        filename: 'bundle.js'
    },
    devServer: {
        contentBase: path.resolve(__dirname, 'dist'),
        publicPath: '/assets/'
    },
    module: {
        rules: [{
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
            loader: 'babel-loader',
            options: {
            presets: ['@babel/preset-env']
            }
        }
        }]
    }
    };
</code>
</pre>


1. create package json
npm init

2. install babel
//converting the es6 version to old js version
npm install @babel/core @babel/cli --save-dev

3. babel preset > set of plugin for certain fatures 
 
npm install @babel/preset-env --save-dev 
npm install --save-dev @babel/preset-env

4. create .babelrc file and set preset / paste the lines
{
    "presets": ["@babel/preset-env"]
}


5. npm run babel - command
package.json: 
 "scripts": {
        "babel": "node_modules/.bin/babel src/index.js -w -o dist/assets/bundle.js"
    },
// node_module , then src.js and -watch -w -o as output then dist js 

6. Webpack  and webpack CLI 
//another approach  for bundle to one file and minify
- for live server
- for bundling javascript


7. npm install webpack webpack-cli --save-dev 
8. create webpack.config.js

const path = require('path');
module.export = {
    entry: './src/index.js',
    output: {
        //D:\wamp\www\test\JavaScript\chapter_1\babel_webpack>
        path: path.resolve(__dirname, 'dist/assets'),
        filename: 'bundle.js'
    }
};
9. //run thsi on CMD: node_modules/.bin/webpack  
10. // but not working, then we need to add to package.json 
   "scripts": {
        "babel": "node_modules/.bin/babel src/index.js -w -o dist/assets/bundle.js",
        "webpack": "node_modules/.bin/webpack -w"
    },

> npm run  webpack

11. stop live server from vs code
12. npm install webpack-dev-server --save-dev
webpack.config.js: add these
 devServer: {
        contentBase: path.resolve(__dirname, 'dist'),
        publicPath: '/assets/'
    }
13. package.json: 
 "serve": "webpack-dev-server"

14. run > npm run serve

15. remove the babel and rename webpacl to build in package json 
"scripts": {

        "build": "node_modules/.bin/webpack",
        "serve": "webpack-dev-server"

    },

16. run>  npm run build

17. install the babel loader to webpack
npm install babel-loader --save-dev 

18. module properties
webpack.config.js file:

  module: {
    rules: [{
      test: /\.js$/,
      exclude: /node_modules/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: ['@babel/preset-env']
        }
      }
    }]
  }
