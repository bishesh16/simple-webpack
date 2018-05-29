# Simple-Webpack
This is a simple webpack 3 tutorial, which should help you familiarize with the basics of webpack.

## Requirements
Node.js 

## Setup

- `npm install`

## Build

- `npm run build` for development mode 

- `npm run build:prod` for production mode

The build commands build our simple app from the `./src` folder and output to `./dist` folder.

## Build in development using webpack-dev-server
- `npm run dev`

This will run webpack in dev mode using webpack-dev-server. It also enables hot reloading, which allows you to
 modify your source code without having to refresh the browser after each change. 

## Run the app with Express server
- `npm run start`

The run command will serve the folder `./dist` using the Express server at http://localhost:3000

## Configuration
Webpack comes with a configuration file with the following structure :
```$json
var config = {
    entry: { ... },
    output: { ... },
    module: {
        rules: [ ...
        ]
    }
}
```
There are mainly three sections on the config file :
- `entry`: defines where your source files are
- `output`: is the folder where webpack create the bundle
- `module/rules` : contains rule to apply for each type of file (i.e .js/ .css, .scss, etc)

## Loaders
- babel-loader for JS files
- style-loader & css-loader for CSS files
- file-loader for HTML files

Here's the complete config for `webpack.config.js`

```$json
var config = {
  context: __dirname + '/src', // `__dirname` is root of project and `src` is source
  entry: {
    app: './main.js',
  },
  output: {
    path: __dirname + '/dist', // `dist` is the destination for the bundle
    filename: 'bundle.js',
  },
  module: {
    rules: [
      {
        test: /\.js$/, // rule for js files
        exclude: /node_modules/,
        loader: "babel-loader" // aply this loader for js files
      }
      ,
      {
        test: /\.css$/,
        use: [
          'style-loader', // the order is very important. it executes in reverse order !!!
          'css-loader' // this is loaded first !!!
        ]
      }
    ]
  }
}
```

