- Create multiple Instances of Tethys in the same machine.
  id:: 626353e0-b9f0-44c4-aba4-c9185da642e7
	- Clone a version of the Tethys Platform: You will porbably need ((626064f7-e8c2-47a9-a645-9f5edb63a9a3))
	- You will need to do add environment variables to the environment.yml
		- Add at the end of the file the following
			- `TETHYS_HOME: <desired_path>`
	- Create an [[conda]] environment with [[mamba]] using the environment.yml
		- `mamba env create -f environment.yml`
	- Run a [[PostgreSQL]] container.
		- ((626357d7-2b13-4902-89f7-94a73712b7d6))
	- Edit the portal_config.yml to have the same configuration as the [[PostgreSQL]] container with the following command [tethys_documentation](http://docs.tethysplatform.org/en/stable/installation/production/manual/configuration/basic/database.html)
		- `tethys settings --set DATABASES.default.NAME tethys_platform --set DATABASES.default.USER <TETHYS_DB_USERNAME> --set DATABASES.default.PASSWORD <TETHYS_DB_PASSWORD> --set DATABASES.default.HOST <TETHYS_DB_HOST> --set DATABASES.default.PORT <TETHYS_DB_PORT>`
	- Run the following command to init the database [tethys_documentation](http://docs.tethysplatform.org/en/stable/installation/production/manual/configuration/basic/database.html)
		- `PGPASSWORD=<POSTGRES_PASSWORD> tethys db configure --username <TETHYS_DB_USERNAME> --password <TETHYS_DB_PASSWORD> --superuser-name <TETHYS_DB_SUPER_USERNAME> --superuser-password <TETHYS_DB_SUPER_PASSWORD> --portal-superuser-name <PORTAL_SUPERUSER_USERNAME> --portal-superuser-email '<PORTAL_SUPERUSER_EMAIL>' --portal-superuser-pass <PORTAL_SUPERUSER_PASSWORD>`
	-
- Integrate [[React.js]]
collapsed:: true
	- Link Ref [here](https://mattsegal.dev/django-react.html)
	- Requirements: install [[node.js]] and [[npm]]
	- Create a new folder called frontend, a src foldder inside this one, and a JS file: `frontend/src/index.js`
	- Inside of the frontend folder, install [[Webpack]] using [[npm]] as follows:
		- ```bash
		  npm init --yes
		  npm install webpack webpack-cli
		  ```
		- Update your .gitignore file to exclude `node_modules` directory.
	- Create the `webpack.config.js` file in the `frontend` directory use the following template:
		- ```javascript
		  // frontend/webpack.config.js
		  const path = require('path')
		  const webpack = require('webpack')
		  module.exports = {
		    // Where Webpack looks to load your JavaScript
		    entry: {
		      main: path.resolve(__dirname, 'src/index.js'),
		    },
		    mode: 'development',fundacion march incas
		    // Where Webpack spits out the results (the myapp static folder)
		    output: {
		      path: path.resolve(__dirname, '../backend/myapp/static/myapp/'),
		      filename: '[name].js',
		    },
		    plugins: [
		      // Don't output new files if there is an error
		      new webpack.NoEmitOnErrorsPlugin(),
		    ],
		    // Where find modules that can be imported (eg. React) 
		    resolve: {
		      extensions: ['*', '.js', '.jsx'],
		      modules: [
		          path.resolve(__dirname, 'src'),
		          path.resolve(__dirname, 'node_modules'),
		      ],
		    },
		  }
		  ```
	- Make [[Webpack]] easy to run by including an entry in the "scripts" section of our `package.json` file:
		- ```json
		  // frontend/package.json
		  {
		    // ...
		    "scripts": {
		      "dev": "webpack --watch --config webpack.config.js"
		    },
		    // ...
		  }
		  ```
		- The --watch flag is particularly useful: it makes Webpack re-run automatically on file change. Now we can run Webpack using npm:`npm run dev`
	- Install [[React.js]] `npm install react react-dom`
	- Adding [[Babel]] `npm install --save-dev babel-loader @babel/core @babel/preset-react`
		- What the hell is all of this? Let me break it down for you:
		- **@babel/core**: The main Babel compiler library
		  **@babel/preset-react**: A collection of React plugins: tranforms JSX to regular JavaScript
		  **babel-loader**: Allows Webpack to use Babel
	- Create a **.babelrc** file in the frontend
		- ```json
		  // frontend/.babelrc
		  {
		      "presets": ["@babel/preset-react"]
		  }
		  ```
	- Edit **webpack.config.js** to use our the Babel compiler for all the JavaScript files:
		- ```JavaScript
		  // frontend/webpack.config.js
		  // ...
		  module.exports = {
		    // ...
		      // Add a rule so Webpack reads JS with Babel
		      module: { rules: [
		      {
		        test: /\.js$/,
		        exclude: /node_modules/,
		        use: ['babel-loader'],
		      },
		    ]},
		    // ...
		  ```
		- **Essentially, this config change tells Webpack: "for any file ending with .js, use babel-loader on that file, expect for anything in node_modules". Finally, we can now use JSX in our React app:**
	- Restart [[Webpack]] for the config changes to be loaded.
	- Deployment
	  I won't cover deployment in detail in this post, because it's long enough already, but in short, you can now deploy your Django/React app as follows:
		- Install JavaScript dependencies with npm
		  Run Webpack to create build artifacts in your Django static files
		  Deploy Django how you normally would
	- There a few things that it would be good to change before deploying, like not using "development" mode in Webpack, but this workflow should get you started for now. If you have never deployed a Django app before, I've written an introductory guide on that as well, which uses the same incremental, explanation-heavy style as this guide.
	- Next steps
	  There is a lot of stuff I didn't cover in this guide, which I'd like to write about in the future. Here are some things that I didn't cover, which are important or useful when building a React/Django app:
		- Hot reloading
		  Deployment
		  Passing requests/data between Django and React
		  Modular CSS / SCSS / styled components
		  Routing and code-splitting
		  Authentication
	-
- Common Error:
	- Error:
		- `line 6, in utc_tzinfo_factory raise AssertionError("database connection isn't set to UTC") AssertionError: database connection isn't set to UTC.`
	- Solution:
		- `mamba install -c conda-forge psycopg2=2.8.6`
		-