# ReactJs_SpringBootCrud

# ReactJs_SpringBootCrud normal build
npm install -g create-react-app

npx create-react-app myfirstreact

cd myfirstreact

npm start

npm creat react-component MyComponent

webpack - toolkit used to compile JavaScript components into a single, loadable bundle

babel - write your JavaScript code using ES6 and compile it into ES5 to run in the browser

axios framework- used to connect react app with spring boot app

sts- window - preferences- http(n/w connection)- Direct
		maven setting.xml from mvn
		
-----------full stack app creating-------------
npx create-react-app frontend-spring-boot-react-crud-full-stack-with-maven

cd frontend-spring-boot-react-crud-full-stack-with-maven
npm start

----------msg convertor error 500--------
solution-

<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.7.4</version>
    <exclusions>
        <exclusion>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-core</artifactId>
        </exclusion>
        <exclusion>
            <groupId>com.fasterxml.jackson.core</groupId>
            <artifactId>jackson-annotations</artifactId>
        </exclusion>
    </exclusions>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-core</artifactId>
    <version>2.7.4</version>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-annotations</artifactId>
    <version>2.7.4</version>
</dependency>
-----------------------
Add the frameworks need to call the REST API - axios, display a form - formik and support routing - react-router-dom

npm add axios -Axios is the libreary which help us to make http request to external resource
npm add react-router-dom ------- It contains DOM bindings for React router
npm add formik -----form library  form validations


---------
Axios is a frontend framework that helps you make

REST API calls with different request methods including GET, POST, PUT, DELETE etc
Intercept Front end REST API calls and add headers and request content
--------------
react-service - by right click

sign with ~ i.e ` is used for variable and string in single place -`${COURSE_API_URL}/instructors/${INSTRUCTOR}`

-----
[Error] Origin http://localhost:3000 is not allowed by Access-Control-Allow-Origin.
Add @CrossOrigin(origins = { "http://localhost:3000", "http://localhost:4200" }) into rest controller

------To enable debug for Front end------
1) goto extension ctlr+shift+X
2) google debug-  debugger for Chrome - install and restart visual studio
3) refresh - new file - .vscode/launch.json
4) remove old code and type chrome -a)chrome launch, b) Attach to chrome change port number to your react running port i.e 3000
5) click on debug mode sign in left side - launch chrome (make sure your react app should be running)- it will open new chrome window which debug
---------------------

==========implement routing========

/src/component/InstructorApp.jsx
-----------
class InstructorApp extends Component {
    render() {
        return (
            <Router> //router is used
                <>
                    <h1>Instructor Application</h1>
                    <Switch>//<Switch> is unique in that it renders a route exclusively. In contrast, every <Route> that matches the location renders inclusively
                        <Route path="/" exact component={ListCoursesComponent} /> //single route to the component
                        <Route path="/courses" exact component={ListCoursesComponent} />
                        <Route path="/courses/:id" component={CourseComponent} />
                    </Switch>
                </>
            </Router>
        )
    }
}
export default InstructorApp

or ex-

import ReactDOM from 'react-dom';
import { Router, Route, Link, browserHistory, IndexRoute } from 'react-router'

example - 
ReactDOM.render((
   <Router history = {browserHistory}>
      <Route path = "/" component = {App}>
         <IndexRoute component = {Home} />
         <Route path = "home" component = {Home} />
         <Route path = "about" component = {About} />
         <Route path = "contact" component = {Contact} />
      </Route>
   </Router>
), document.getElementById('app'))
----------------------------------
example - https://github.com/ReactTraining/react-router/blob/master/packages/react-router/docs/api/Switch.md
---------
error- TypeError: Cannot read property 'location' of undefined

@@@@-----npm install react-router

---You're doing a few things wrong.

First, browserHistory isn't a thing in V4, so you can remove that.

Second, you're importing everything from react-router, it should be react-router-dom.

Third, react-router-dom doesn't export a Router, instead, it exports a BrowserRouter so you need to import { BrowserRouter as Router } from 'react-router-dom.
-------------
`npm run build`---

-----------merge react app into Boot app-------
1.)`npm run build`
2.) Copy data from build folder of react
3.) Paste into springboot main/resources folder
4.) run spring boot app
===============================
babel and webpack
---------------
https://www.tutorialspoint.com/reactjs/reactjs_environment_setup.htm

1)npm install webpack --save
npm install webpack-dev-server --save
npm install webpack-cli --save

2)Install babel -
npm install babel-core --save-dev
npm install babel-loader --save-dev
npm install babel-preset-env --save-dev
npm install babel-preset-react --save-dev
npm install html-webpack-plugin --save-dev

3)Create the Files - if not exist
C:\Users\username\Desktop\reactApp>type nul > index.html
C:\Users\username\Desktop\reactApp>type nul > App.js
C:\Users\username\Desktop\reactApp>type nul > main.js
C:\Users\username\Desktop\reactApp>type nul > webpack.config.js
C:\Users\username\Desktop\reactApp>type nul > .babelrc

4)Set Compiler, Server and Loaders
Open webpack-config.js file and add the following code. We are setting webpack entry point to be main.js. Output path is the place where bundled app will be served. We are also setting the development server to 8001 port. You can choose any port you want.


5)package.json - scripts
"start": "webpack-dev-server --mode development --open --hot",
"build": "webpack --mode production"

6)index.html
This is just regular HTML. We are setting div id = "app" as a root element for our app and adding index_bundle.js script, which is our bundled app file.

our root App element, inside index.js

7)Create a file with name .babelrc 
{
   "presets":["env", "react"]
}

8) Running the Server- npm start
error-
npm installbabel-preset-es2015 --save-dev
npm install @babel/core @babel/preset-env

"@babel/preset-es2015": "^7.0.0-beta.53",
    "@babel/preset-react": "^7.7.4",
	
	"devDependencies": {
    "@babel/core": "^7.7.7",
    "@babel/preset-env": "^7.7.7",
    "babel-loader": "^8.0.6",
    "webpack": "^4.41.4",
    "webpack-cli": "^3.3.10"
  }
===========================================================================================

# ReactJs_SpringBootCrud with babel and webpack
https://medium.com/@siddharthac6/getting-started-with-react-js-using-webpack-and-babel-66549f8fbcb8

https://blog.bitsrc.io/setting-a-react-project-from-scratch-using-babel-and-webpack-5f26a525535d

STEPS-
1)Create our application directory "app" and cd app into it. 

2)npm init and finish the process. package.json should get created inside (current)app directory

3)npm i -S react react-dom

4)Install Babel packages as dev dependency, 
npm i -D babel-core babel-loader babel-preset-env babel-preset-react


5)Install Webpack packages as dev dependencies
npm i -D webpack webpack-cli webpack-dev-server html-webpack-plugin

6) Update the package.json/webpack-config.js/.babelrc dependencies according to below formate.

NOTE : BABEL CORE AND BABEL LOADER VERSION IS IMPORNTANT THING TO NOTICE

=======================Babel 6.x ('babel-core') with 'babel-loader@7' ================================
Error: Cannot find module 
'@babel/core'
 babel-loader@8 requires Babel 7.x (the package '@babel/core'). If you'd like to use Babel 6.x ('babel-core'), you should install 'babel-loader@7'

 -------package.json-------------
 {
  "name": "reactapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server --mode development --open --hot",
    "build": "webpack --mode production"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^16.12.0",
    "react-dom": "^16.12.0"
  },
  "devDependencies": {
    "babel-core": "^6.26.3",
    "babel-loader": "^7.1.5",
    "babel-preset-env": "^1.7.0",
    "babel-preset-react": "^6.24.1",
    "html-webpack-plugin": "^3.2.0",
    "webpack": "^4.41.5",
    "webpack-cli": "^3.3.10",
    "webpack-dev-server": "^3.10.1"
  }
}
---------------webpack-config.js-------
const path = require('path');
const HWP = require('html-webpack-plugin');

module.exports = {
    entry: path.join(__dirname, '/src/index.js'),
    output: {
        filename: 'build.js',
        path: path.join(__dirname, '/dist')
    },
    module:{
        rules:[
        {
           test: /\.js$/,
           exclude: /node_modules/,
           loader: 'babel-loader'
        }]
    },
    plugins:[
       new HWP(
           {template: path.join(__dirname,'/src/index.html')}
        )
    ]
}
---------------.babelrc------------
{"presets":["env", "react"]}
---------------------------------

=======================Babel 7.x ('babel-core') with 'babel-loader@8' ================================
ERROR in ./src/index.js
Module build failed (from ./node_modules/babel-loader/lib/index.js):
Error: Cannot find module 'babel-preset-env' from 'D:\react\ReactApp\reactApp'
- Did you mean "@babel/env"?


 -------package.json-------------
 {
  "name": "reactapp",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "webpack-dev-server --mode development --open --hot",
    "build": "webpack --mode production"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "react": "^16.12.0",
    "react-dom": "^16.12.0"
  },
  "devDependencies": {
    "@babel/core": "^7.7.7",
    "@babel/preset-env": "^7.8.3",
    "@babel/preset-react": "^7.7.4",
    "babel-loader": "^8.0.6",
    "html-webpack-plugin": "^3.2.0",
    "webpack": "^4.41.5",
    "webpack-cli": "^3.3.10",
    "webpack-dev-server": "^3.10.1"
  }
}

---------------webpack-config.js-------
const path = require('path');
const HWP = require('html-webpack-plugin');

module.exports = {
    entry: path.join(__dirname, '/src/index.js'),
    output: {
        filename: 'build.js',
        path: path.join(__dirname, '/dist')
    },
    module:{
        rules:[
        {
           test: /\.js$/,
           exclude: /node_modules/,
           loader: 'babel-loader'
        }]
    },
    plugins:[
       new HWP(
           {template: path.join(__dirname,'/src/index.html')}
        )
    ]
}
---------------.babelrc------------
{"presets":["@babel/env", "@babel/react"]}
---------------------------------
npm start
npm run build - it will create one index.html and one index_bundle.js file
this two files we need to paste into java/resources/static folder

--------------https://blog.bitsrc.io/setting-a-react-project-from-scratch-using-babel-and-webpack-5f26a525535d
ERROR in ./src/App.css 1:0
Module parse failed: Unexpected character '@' (1:0)
You may need an appropriate loader to handle this file type, currently no loaders are configured to process this file. See https://webpack.js.org/concepts#loaders
> @import url(https://unpkg.com/bootstrap@4.1.0/dist/css/bootstrap.min.css)

solution - provide entry into webpack-config.js as-
module{ rules[
	{
            test: /\.css$/,
            use: [
               "style-loader",
               {
                  loader: "css-loader",
                  options: {
                     modules: true
                  }
               }
            ]
    },
]}
------------------
