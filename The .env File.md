
The `.env` file is a hidden file that is used to pass environment variables to your application.

This file is secret, no one but you can access it, and it can be used to store data that you want to keep private or hidden.

*example*, you can store API keys from external services or your database URI. You can also use it to store configuration options

By setting configuration options, you can change the behavior of your application, without the need to rewrite some code.



The environment variables are accessible from the app as `process.env.VAR_NAME`.

`process.env` object is a global Node object, and variables are passed as strings.

By convention, the variable names are all uppercase, with words separated by an underscore. 

The `.env` is a shell file, so you don’t need to wrap names or values in quotes. It is also important to note that there cannot be space around the equals sign when you are assigning values to your variables, e.g. `VAR_NAME=value`. 

Usually, you will put each variable definition on a separate line.

 