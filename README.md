# vue-webpack-4
configuring vue js and other plugins and loaders with webpack 4

``` js
const path = require('path');
const outputPath = path.resolve( __dirname, 'dist');
const { VueLoaderPlugin } = require('vue-loader')
const HtmlWebPackPlugin = require("html-webpack-plugin");

function resolve (dir) {
    return path.join(__dirname, './src', dir)
}

module.exports = {
    entry: {
        app: './src/index.js'
    },
    output: {
        path: outputPath,
        filename: './js/[name].js',
        publicPath: '',
    },

    resolve: {
        extensions: ['.js', '.vue', '.json'],
        alias: {
            '@components': resolve('components'),
            '@directives': resolve('directives'),
            '@helpers': resolve('helpers'),
            '@router': resolve('router'),
            '@store': resolve('store'),
            '@src': resolve('')
        }
    },

    module: {
        rules: [

            {
                test: /\.vue$/,
                loader: 'vue-loader',
                options: {
                    loaders: {
                        js: 'babel-loader',
                    }
                },
            },

            {
                test: /\.less$/,
                use: [{
                    loader: "style-loader" // creates style nodes from JS strings
                }, {
                    loader: "css-loader" // translates CSS into CommonJS
                }, {
                    loader: "less-loader" // compiles Less to CSS
                }]
            },

            {
                test: /\.scss$/,
                use: [
                    'vue-style-loader',
                    'css-loader',
                    'sass-loader'
                ]
            },

            {
                test: /\.js$/,
                exclude: /node_modules/,
                use: {
                    loader: "babel-loader"
                }
            },

            {
                test: /\.html$/,
                use: [
                    {
                        loader: "html-loader",
                        options: { minimize: false }
                    }
                ]
            }

        ]
    },

    plugins: [
        new VueLoaderPlugin(),
        new HtmlWebPackPlugin({
            template: "./src/index.html",
            filename: "index.html",
            inject:false
        }),

    ]
};
