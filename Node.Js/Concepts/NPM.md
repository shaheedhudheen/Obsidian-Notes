
### Package Scopes

Generally, most npm packages should be installed locally—this way, among other reasons, each project can control which specific versions of its dependencies it uses. That being said, there are a few other ways you might install packages

#### devDependencies

While most dependencies play a direct role in the functionality of your application, _development dependencies_ are used for the purpose of making development easier or more efficient.

**Eg**: , the `nodemon` package is actually better suited as a development dependency since it makes developers’ lives easier but makes no changes to the app itself.

 `--save-dev` flag, or its alias, `-D`.

Development dependencies are listed in the `"devDependencies"` field of the **package.json** file. This indicates that the package is being used specifically for development and will not be included in a production release of the project.

#### Global Packages

Some packages can be installed _globally_ meaning they are available system-wide, without the need to install it each time you create a new application. 
Typically, packages installed this way will be used in the command-line rather than imported into a project’s code. One such example is the [`http-server` package](https://www.npmjs.com/package/http-server) which allows you to spin up a zero-configuration server from anywhere in the command-line.

To install a package globally, use the `-g` flag

#### npm install

```
npm i
```

Running this command will automatically install all packages listed as dependencies or development dependencies. If you wish to leave out development dependencies, you can run the command with the `--production` flag.

```
npm i --production
```

Because of this convenient command, it is recommended that you do not include your local **node_modules/** folder in any repository that you use to store and share your code to avoid taking up precious storage resources.

