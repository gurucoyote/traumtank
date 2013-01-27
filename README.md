# Traumtank bare bone proof of concept
The goal of this repo at this stage is to illustrate how to use a local RESTful webserver with brower based editing of text files.

The RESTful server in this case is Mongoose, one of the iimost lightweight webservers out there. It is fully cross-platform and writte in two C files that can be easily compiled and build on most platforms that have a C compiler.

## Why do we need a server at all?
The whole point of this project is to illustrate a all-in-browser content creation. The only reason why a (local) server is needed here is the fact that browers do not have write access to the local filesystem... so we could load files, edit them and... well not save our work.

This is where the lightweight mongoose comes in. Its very small and has not extra dependencies (it vompiles from two C files). It is still very powerfull and most importantly it can act as a RESTful server (it does GET, PUT and DELETE, implementiong basic WebDAV features).

## Client side
The (very simple) client uses the jQuery `$.ajax()` features to load and save (text) files from the www folder. The client (rest.html) is kept intentionally minimalistic for this stage for illustration. A lot can (and will) be done to extend this bare concept. See the maim Traumtank branch for that.

## Setup and Usage
There are only a few steps to get going. 

1. Start mongose server<pre>
	cd mongose/
	make mac
	# or make linux, make mingw etc
	./mongose conf.txt</pre>
2. Visit `http://localhost:8082/rest.html` in your browser. You will need to login. The default username and password is «admin« and «admin«.
3. Write some text, and then hit Save. Note the input field for the filename (and path). This is where the file will end up on your local disk. 
> Note: you CAN NOT go out of your `www/` folder. 
Paths like `../../somefile.txt`
will simply end up in the top level folder (`www/`).

## Credits
* [The mongose web server](https://github.com/valenok/mongoose)
  >Note: this is not the same mongose as the Node.js related one. Names!
* [jQuery](http://jquery.com)