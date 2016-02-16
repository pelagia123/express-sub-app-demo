# Express Sub-App Demo

An extreme example of separating what may have been a single Expres app
into multiple applications with a host to bring them back together.

## About This Demo

Express is one of the most flexible web hosting libraries I have used in
my career. I love how simple it can be, and how it allows you to grow your
system as needed. 

One of the areas that has continued to bother me in my own code, is my
lack of ability to cleanly separate different parts of my express app while
having those parts hosted in the same root domain name. 

#### Prior Attempts To Separate Code

Previously, I had separated what may have been a `/admin` route into a 
completely separate sub-domain, like `http://admin.example.com`. 

With the realization that Express application instances can be mounted into
other Express application instances, however, that changed. 

While I do see value in moving `/admin` out to a separate sub-domain, still,
I also see a lot of value in separating `/admin` into it's own project folder
and still mounting it as `/admin` in the main Express app.

This repository is a demonstration Express' ability to do just that - to take
what would have been cluttered code from multiple route paths, separate them
into their own application instance, and bring them back together in a single
application host. 

#### On Being An "extreme" Example App

I call this an "extreme example" because I have purposely taken the separation
out to the edge of what I might consider useful. Taking this to an extreme allows
us to see the bounds of where this might be useful. 

It is still possible to take this separation of apps further, creating more
sub-applications to split further responsibilities apart. However, this might
really jump the bounds of usefulness... depending on your circumstances, of
course. :)

## Running The Demo

Clone the repository, then 

* `npm install` from the root folder
* `npm start` from the root folder
  * alternatively: run `./host/bin/www` 

## Project Structure

This demo project is split up into multiple Express application instances,
each of which handles a specific portion of the over-all web application.

The sub-application instances include:

* `api`: handles the JSON based API access for the app
* `errors`: handles root level 404 and route / middleware errors
* `host`: the actual web server into which the other apps are mounted
* `web`: the core web pages for browser based usage

You'll note in each of these projects, that various parts of the default
Express app (as generated by the Express-Generator project) have been removed.

For example, the `api` project does not need to render any Jade views, so the
view engine registration and views folders have been removed from this project.
Similarly, none of the sub-applications need to have actual web server code
from the bin/www file - only the `host` application needs this. 

By separating the application into multiple sub-apps, code is easier to
maintain as it contains less clutter from unrelated things. 

## Legal Junk

Copyright &copy;2016 Muted Solutions, LLC. All Rights Reserved.

Distributed under [MIT License](http://mutedsolutions.mit-license.org).
