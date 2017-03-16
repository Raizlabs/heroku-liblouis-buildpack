Heroku buildpack
===================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for makefiles.
It uses [Make](http://www.gnu.org/software/make/).
This is a fork from http://github.com/heroku/heroku-buildpack-c.git and is custom configured to install LibLouis from the vendor directory on a heroku application.

Setup
-----

**In your heroku application**
Download the liblous tarball from http://liblouis.org/downloads/

Copy the extracted contexts to your application's root directory `vendor/liblouis`

Create an additional directory `vendor/liblous-exec` and add a `.gitkeep` file

Add a `.profile` file to your root directory with `export LD_LIBRARY_PATH=$HOME/vendor/liblouis-exec/lib` inside

Add this buildpack to your heroku application with `heroku buildpacks:add https://github.com/Raizlabs/heroku-liblouis-buildpack`

Commit your changes, and push them up to your heroku application `git push heroku master`


Usage
-----

Example usage:

    $ heroku buildpacks:add http://github.com/kida001/heroku-buildpack-c.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Configuring
    -----> Compiling with Make
    -----> Installing with Make
